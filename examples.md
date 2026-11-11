# 合规示例集（standard v3.1 条款实例化）

> 定位：standard.md v3.1 全部条款（D1–D13 / N1–N7 / F1–F16 / M1–M26 / §6 骨架 / §7 迁移）的示范实例。
> 用法：新建项目时复制对应骨架，按 D8 登记后裁剪；示例随条款版本更新，条款变更时同步修订本文件。
> 树内括注 = 依据条款号。

## 例一（主示例）：生物信息研发项目——全场景触发

项目：cfDNA 甲基化组织特异性 panel 研发（数据 + 代码 + 湿实验 + 受试者 + 专利布局，触发核心条款全量 + §9 + §10 + §11）。

### 1. 项目根目录树

```text
methylation_panel_dev/                     # 项目根（N1 snake_case；组合逻辑：外层功能）
│
├─ README.md                               # M1 结构表+命名约定+缩写表+保管期限表
├─ .gitignore                              # D7 白名单式（见 §6）
│
├─ configs/                                # M20 路径与参数唯一出口
│  ├─ paths.yaml                           #   全库路径定义（脚本禁裸写绝对路径）
│  └─ gates_v1.0.yaml                      #   冻结参数（版本随代次，M22 精神）
│
├─ data_GSE186458/                         # N2 登录号原样；§1 对象逻辑；F12 build 由 README 声明
│  ├─ <原始 bigWig ×N>                     # D1 只读；M8 入库即校验
│  ├─ README.md                            # M8 来源/日期/文件数/大小/MD5/版本/用途限制
│  └─ MANIFEST.md5                         # M4
│
├─ data_hg38/                              # M22 参考数据版本目录化（build 即目录名）
├─ data_gnomad_v3.1.2/                     # M22 版本入名；目录内禁止替换文件
│
├─ data_VendorX-Lot2026A/                  # N2 厂商批次号原样；§11 湿实验触发
│  ├─ <FASTQ/BCL 原始文件…>                # M8 认证真实副本（不拆包不改结构）
│  └─ README.md                            # M17 五件套+M11 人遗登记（见 §4）
│
├─ subject-linkage/                        # F11 编号-身份映射受控目录
│                                          #   D12 chmod 700；不入 git；机密级
├─ scripts/
│  ├─ shared/
│  │  └─ gates.py                          # 共享模块（非流程件，N5 编号不适用）
│  ├─ kidney-line/                         # 线目录（线名=一个语义域，'-' 域内连接）
│  │  ├─ kidney01_ingest.py                # N5/F8 编号=执行顺序，零填充
│  │  ├─ kidney02_segment.py
│  │  ├─ kidney02b_re-segment.py           # N5 插入步骤用字母后缀居中（06b 同理）
│  │  └─ kidney03_score.py
│  └─ liver-line/
│     └─ liver01_ingest.py
│
├─ tests/                                  # D10 测试与生产分离
│  ├─ test_gates.py
│  └─ fixtures/
│     └─ region_small_hg38.tsv             # 小型 fixture；禁反向流入 raw 层
│
├─ 01_intermediate/                        # N5 生命周期层编号；D2 可重建；D7 不入 git
│  └─ run_31426_20261111-143052/           # §1 逻辑4 run_{PID}_{YYYYMMDD-HHMMSS}
│     ├─ segments_kidney_hg38.tsv          # F12 坐标件带 build
│     ├─ segments_kidney_hg38.tsv.tbi      # D9 伴随件成组
│     └─ run_meta.yaml                     # D2 软件版本/参数/种子+PRNG/MANIFEST 引用
│
├─ 02_final/
│  ├─ panel_markers_hypo_v2.0.tsv          # F2 定型产物版本号末段
│  ├─ panel_markers_hyper_v2.0.tsv
│  └─ delivery_panel-v2.0_20261120/        # §8 交付包独立目录+MANIFEST.md5
│     └─ MANIFEST.md5                      #   交付后 D11 封存（chmod -R a-w）
│
├─ docs/
│  ├─ RUNBOOK.md
│  ├─ design-input_panel-spec_v1.0.md      # M13 设计输入文档位
│  ├─ traceability_matrix_20261115.tsv     # M15 溯源矩阵（含 CAPA 挂靠列）
│  ├─ VAL-RPT-017-v3_panel-performance.pdf # F16 受控文档编号
│  ├─ report_donor-origin_final_20261115.pdf       # F14 报告链
│  └─ report_donor-origin_amended01_20261120.pdf   #   amended 不覆盖 final
│
├─ logs/                                   # M9 运行输出驻地（总量上限见 M14）
│  └─ kidney03_score_run31426_20261111-143052.log
│
├─ explore/                                # D5 探索性内容驻地（不散落根层）
│  └─ scaling-test_20261015/
│
├─ archive/                                # D6 归档=历史代次（永久，仅供追溯）
│  └─ v1-markers-20260301/
│     ├─ README.md                         #   沿革+「非现行输入」声明
│     └─ MANIFEST.md5
│
└─ backup/                                 # D6 修复轮基线（与 archive 语义分立）
   └─ pre_direction-fix_20260911/          #   命名 pre_<缺陷>_<日期>；验证通过后可清理
```

### 2. 文件命名实例（F 条款逐条落位）

| 实例 | 依据 |
|------|------|
| `panel_markers_hypo_v2.0.tsv` | F2 模板+版本末段；F1c 裸限定词禁用（非 `final`）；F5 小写；F9 .tsv |
| `gse275017_beta-contribution_ranking_20261111.tsv` | F3 数据集域`_`属性域（beta-contribution 域内`-`）`_`操作域`_`日期域 |
| `segments_kidney_hg38_20261111.tsv` | F12 坐标件带 build；F4 ISO 8601 紧凑式 |
| `kidney01_ingest.py` / `kidney02b_re-segment.py` | F8 线内编号；N5 字母后缀插入 |
| `run_31426_20261111-143052/` | §1 逻辑4 同日多 run 免人工序号 |
| `report_donor-origin_final_20261115.pdf` → `…_amended01_…` | F14 报告修订链+快照日期 |
| `VAL-RPT-017-v3_panel-performance.pdf` | F16 受控编号 `<类别>-<序号>-v<版本>`（域内`-`连接） |
| `pre_direction-fix_20260911/` | D6 backup 命名规范 |
| `contract…_signed.pdf`（例三） | F2 对象_属性_日期_状态 |
| `gse186458_wbc-annotation_v1.2_20261101_02.tsv` | F2 同日多版本 `_日期_序号` |

### 3. README.md 结构表（M1 + D13 + M25 三机制合一张表）

| 目录/文件 | 用途 | status | owner | 分级 | 保管期限 |
|-----------|------|--------|-------|------|----------|
| data_GSE186458 | 公共甲基化数据集（21 器官 bigWig） | active | yzhuang | 内部 | 项目归档+5 年 |
| data_VendorX-Lot2026A | 厂商靶向甲基化测序下机包（M17/M11） | active | yzhuang | 受限 | ≥10 年（GCP） |
| data_hg38 / data_gnomad_v3.1.2 | 参考数据（版本目录化） | active | yzhuang | 内部 | 随代次更新 |
| subject-linkage | 受试者编号-身份映射（F11） | active | yzhuang | 机密 | 10 年；不入 git、不入共享 |
| 01_intermediate | 可重建中间产物 | active | yzhuang | 内部 | final 验证后按 M14 清理 |
| 02_final | 终产物与交付包 | active | yzhuang | 内部 | 永久（panel 代次） |
| archive/v1-markers-20260301 | 已废弃 v1 代次 | archived | yzhuang | 内部 | 永久（仅供追溯） |
| explore/scaling-test_20261015 | 探索产物 | dormant（6 个月无更新） | yzhuang | 内部 | 定期盘点处置 |

### 4. data_VendorX-Lot2026A/README.md（M17 五件套 + M11 人遗登记）

```markdown
# data_VendorX-Lot2026A — 靶向甲基化测序下机包（认证真实副本）
- 来源机构：××测序公司（回传包原样入库，未拆改）
- 入库日期：2026-11-05；文件数：24；总大小：21.5 GB；MD5 清单：MANIFEST.md5
- M17 五件套：
  ① 仪器原始输出：BCL→FASTQ 直录入库，未经人工转录
  ② 试剂/耗材 lot：Library-Kit lot#20260812A、Conversion-Enzyme lot#20260901B
  ③ protocol 版本：bisep-v1.2
  ④ 储存条件：-80 °C，冻融 1 次
  ⑤ 操作者与日期：×××，2026-11-05
- M11 人遗登记：样本来源机构××医院；伦理批号××-2026-017；人遗备案号××
- 用途限制：仅限本 panel 研发验证，禁止出境与二次分发
```

### 5. configs/paths.yaml（M20）

```yaml
# M20 路径唯一出口——脚本一律 from configs import paths，禁止裸写绝对路径
raw:
  gse186458: /data3/projects/methylation_panel_dev/data_GSE186458
  vendorx_lot2026a: /data3/projects/methylation_panel_dev/data_VendorX-Lot2026A
ref:
  hg38: /data3/projects/methylation_panel_dev/data_hg38
  gnomad: /data3/projects/methylation_panel_dev/data_gnomad_v3.1.2
out:
  intermediate: /data3/projects/methylation_panel_dev/01_intermediate
  final: /data3/projects/methylation_panel_dev/02_final
logs: /data3/projects/methylation_panel_dev/logs
```

### 6. 流程台账（M2，scripts_registry.tsv）

| 脚本 | 线 | 输入 | 输出 | 验证状态 |
|------|----|------|------|----------|
| kidney01_ingest.py | kidney-line | data_GSE186458/*.bw | 01_intermediate/run_…/beta_raw.npz | 已验证（md5 复跑一致） |
| kidney02_segment.py | kidney-line | beta_raw.npz | segments_kidney_hg38.tsv | 已验证 |
| kidney03_score.py | kidney-line | segments + gates_v1.0.yaml | 02_final/panel_markers_*.tsv | 已验证（性能达标） |

### 7. .gitignore（D7 白名单式）

```gitignore
/*                  # D7：默认排除一切
!.gitignore
!README.md
!configs/
!scripts/
!tests/
!docs/
```
（data_*、subject-linkage/、01_intermediate/、02_final/、logs/、explore/、backup/ 自动排除；archive/ 仅 README 与 MANIFEST 需要时显式纳入）

### 8. 原子创建序列（§6 实测命令）

```bash
# ③ 一条 mkdir -p 建全骨架（不留半成品）
mkdir -p methylation_panel_dev/{configs,scripts/{shared,kidney-line,liver-line}, \
  tests/fixtures,01_intermediate,02_final,docs,logs,explore,archive,backup}
mkdir -p methylation_panel_dev/subject-linkage
# ⑤ 空目录占位
touch methylation_panel_dev/{tests/fixtures,logs,explore,archive,backup,subject-linkage}/.gitkeep
# ④ 权限落地（D12；数据入库后另执行 chmod -R a-w data_*）
chmod 700 methylation_panel_dev/subject-linkage
# ⑥⑦ 登记（写 README 结构表/台账）→ git 首提（结构基线）
cd methylation_panel_dev && git init && git add -A \
  && git commit -m "init: scaffold per directory-management standard v3.1"
```

## 例二：软件工程项目（§12 场景）

```text
sprint-board-api/
├─ README.md
├─ configs/                       # M20（环境地址、特性开关）
├─ src/sprint-board-api/          # 代码
├─ schemas/
│  ├─ task_v2.json                # M26 schema 版本化；破坏性变更升 v3 并附迁移脚本
│  └─ task_v3.json
├─ tests/fixtures/                # D10
├─ docs/
│  └─ api-spec_v1.3.md            # F2 版本末段
├─ artifacts/                     # M9 CI 构建产物；gitignore；不入正式结果层
├─ logs/
├─ archive/
├─ CHANGELOG.md                   # F16 对应 git tag
└─ .gitignore                     # D7
```

关键点：依赖锁定 D2（lockfile/镜像 digest 入库）；数据管道场景加 §1 生命周期分层（data/bronze|silver|gold 即 01/02 编号变体）；M16 幂等重跑（make/Snakemake 检查点）。

## 例三：行政/合同档案项目（§14 场景，非数据型裁剪出口）

```text
contracts-2026/
├─ README.md                      # M1 结构表 + M25 保管期限表
├─ docs/
│  ├─ incoming/                   # §1 逻辑6 流向：来件
│  │  └─ contract_supplier-alpha_nda_20260301_received.pdf
│  └─ outgoing/                   # 去件
│     └─ contract_supplier-alpha_nda_20260301_signed.pdf
│        # F2 对象_supplier-alpha(域内-) _属性_日期_状态；F15 用对方法定名称
├─ legal-hold/                    # M25 litigation hold：挂起期间禁销毁，README 注明案件号
└─ archive/
   └─ fy2024/
      └─ MANIFEST.md5             # M4
```

关键点：受控编号 F16（`CT-2026-041-v2`）；保管期限按会计档案管理办法 10/30 年或合同约定期；正式签署件 D11 封存思维（只读存档，修订走新文件）。

## 例四：最小文档/设计项目（§6 最深裁剪）

```text
portfolio/
├─ README.md                      # 结构表（裁剪后仍须登记）
├─ docs/
│  ├─ logo_v1.png / logo_v2.png   # F2 代际版本号末段
│  └─ brand-guide_v1.1.md
└─ archive/
```

核心条款仍适用：D8 登记、F1–F3 命名、D6 归档、M1 README；数据层/生命周期层按 §6 裁剪声明省略并在 README 记录偏离。

## 反例速查（不合法命名与结构）

| 反例 | 违反 | 正解 |
|------|------|------|
| `Final Report v2 (copy).pdf` | N3 空格括号；F1c 裸限定词+copy；F5 大写 | `panel_report_final_v2.pdf` |
| `final/`、`new/`、`temp/` | F1c/N6 裸限定词 | `02_final/`、`explore/scaling-test_…/` |
| `数据_2026.xlsx` | N3 中文名 | `beta_matrix_20261111.tsv` |
| `markers.tsv`（坐标无 build） | F12 | `markers_kidney_hg38_v2.0.tsv` |
| `markers_v3.2.1.tsv` | F2 三段式版本 | `markers_v3.2.tsv` |
| `phase1_hyper.py` | N5/F8 非零填充（新建件） | `phase01_hyper.py`（存量按 F5 冻结） |
| `Kidney_Markers/` | N1 大写 | `kidney-markers/` 或并入线目录 |
| `liver & kidney panel.xlsx` | N3 & 与空格 | 拆两文件或 `panel_liver-kidney_…` |
| `hg19_hg38_merged.bed` | F12 build 混合无主次 | `markers_hg38_to_hg19.bed` |
| `run_3/` 与 `run_10/` 混排 | §1 逻辑4/N5 宽度 | `run_{PID}_{YYYYMMDD-HHMMSS}` |
| 旧路径长期留软链接"以防万一" | §7 别名禁令 | 登记入迁移日志+限期（≤7 天）回收 |
| `patient_张三_beta.tsv` | F11 可识别信息 | `subject_S042_beta.tsv`（映射入 subject-linkage/） |
