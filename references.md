# 引用来源汇总（standard.md 条款依据）

## 一、目录组织与数据科学最佳实践

- Cookiecutter Data Science（数据科学项目结构事实标准）— https://cookiecutter-data-science.drivendata.org
- A Quick Guide to Organizing Computational Biology Projects（Noble 系，计算生物学金标准）— https://connect.h1.co/article/720907672
- A Quick Guide for Building a Successful Bioinformatics Project（Budd 2015, PMC4318577）— https://pmc.ncbi.nlm.nih.gov/articles/PMC4318577
- Software Carpentry: Project Organization and Management for Genomics — https://swc-uiuc.github.io/organization-genomics
- Axiom Data Science: Data Organization（深度≤3、文件名优先于嵌套）— https://www.axiomdatascience.com/best-practices/DataOrganization.html
- Reproducible Data Science: Project Organization — https://ecorepsci.github.io/reproducible-science/project-organization.html
- vdsbook: Setting Up Your Data Science Project（一致性>具体形态）— https://vdsbook.com/03-code_reproducibility
- Harvard Medical School: Directory Structure（属性分维）— https://datamanagement.hms.harvard.edu/plan-design/directory-structure
- Nanopore4edu: Data Organization and Management — https://nanopore4edu.org/bioinformatics/data_management

## 二、文件命名规范

- UBCO Biology: What's in a name（三性：human/machine readable + sortable）— https://ubco-biology.github.io/Procedures-and-Guidelines/whats-in-a-name.html
- UBCO Biology: Directory Structures — https://ubco-biology.github.io/Procedures-and-Guidelines/directory-structures.html
- HSLS Pitt: 5 Simple Ways to Love Your Data（ISO 8601）— https://info.hsls.pitt.edu/updatereport/2020/february-2020/5-simple-ways-to-love-your-data
- ISTP Metadata: File and Dataset Naming — https://istp-metadata.readthedocs.io/en/v1.0.0/source/filenaming-dataset-naming-recommendations.html

## 三、数据工程分层

- Databricks: What is Medallion Architecture — https://www.databricks.com/blog/what-is-medallion-architecture
- Microsoft: The medallion lakehouse architecture — https://learn.microsoft.com/en-us/azure/databricks/lakehouse/medallion
- Google Cloud: What Is Medallion Data Architecture — https://cloud.google.com/discover/what-is-medallion-architecture

## 四、临床试验与 GxP 法规

- ALCOA+ 数据完整性：Quanticate — https://www.quanticate.com/blog/alcoa-principles ；CASRAI — https://casrai.org/guides/what-is-data-integrity ；traqx — https://traqx.io/en/blog/alcoa-plus-data-integrity
- 21 CFR Part 11：FDA 官方指南 — https://www.fda.gov/media/75414/download ；eCFR 法规文本 — https://www.ecfr.gov/current/title-21/chapter-I/subchapter-A/part-11 ；SimplerQMS 审计追踪 — https://simplerqms.com/21-cfr-part-11-audit-trail
- HIPAA 去标识化：NCBI Concepts and Methods for De-identifying Clinical Trial Data — https://www.ncbi.nlm.nih.gov/sites/books/NBK285994 ；Safe Harbor 18 标识符 — https://www.accountablehq.com/post/what-is-the-hipaa-de-identification-safe-harbor-definition-18-identifiers-and-examples ；Network for Public Health Law — https://www.networkforphl.org/wp-content/uploads/2020/01/De-Identification_HIPAASafeHarbor-10-1-19.pdf
- CDISC/eCTD：SDTM — https://www.cdisc.org/standards/foundational/sdtm ；FDA Study Data Technical Conformance Guide — https://www.fda.gov/media/136460/download
- NMPA 临床试验数据管理工作技术指南（2016）— https://www.nmpa.gov.cn/xxgk/ggtg/ypggtg/ypqtggtg/20160729183801891.html?type=pc&m=
- 人类遗传资源：科技部国际合作临床试验备案 — https://fuwu.most.gov.cn/r/cms/zwpt/web/assets/pdf/7.rlyczygjhzlcsybafwhcx.pdf ；国家卫健委科教司常见问题（2025-03）— https://www.nhc.gov.cn/qjjys/rlyczygl/202503/39a747744f2242068fdaf39b0452e11e.shtml
- 临床试验电子文件命名：Melbourne Children's Trial Centre MCTC076 V2.0 — https://metis.melbournechildrens.com/media/ohqjvolo/mctc076_guidance_electronic-file-naming-conventions.pdf

## 五、研发记录、专利与设计开发

- ELN 规范：Harvard Medical School — https://datamanagement.hms.harvard.edu/collect-analyze/electronic-lab-notebooks ；NIH Intramural ELN Policy — https://oir.nih.gov/sourcebook/intramural-program-oversight/electronic-lab-notebooks/intramural-electronic-lab-notebook-policy ；IDBS（GLP 合规）— https://www.idbs.com/knowledge-base/how-do-electronic-laboratory-notebooks-elns-improve-data-management-and-regulatory-compliance
- 专利证据：UM Ventures Lab Notebooks — https://www.umventures.org/for-inventors/inventor-resources/lab-notebooks-protecting-your-intellectual-property ；Wiggin LLP Laboratory Record Keeping（发明日期判例）— https://www.wiggin.com/publication/laboratory-record-keeping ；UTA Lab Notebook Procedure（证人签名=发明日期）— https://resources.uta.edu/research/regulatory-services/rcr/lab-notebook-procedure.php ；TimeBinder 时间戳存证 — https://timebinder.io/invention-records-timestamping ；Let's Seal — https://letsseal.org/site/use-cases/intellectual-property
- 设计开发文档（DHF/技术文档）：CloudtheApp DHF Definition — https://www.cloudtheapp.com/glossary/glossary-design-history-file-dhf ；MPO Magazine（DHF vs Technical File）— https://www.mpo-mag.com/exclusives/overview-of-the-medical-device-design-history-file-technical-file-and-design-dossier ；EU IVDR 2017/746 全文 — https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32017R0746 ；NAMSA EU 技术文档 — https://namsa.com/services/consulting/eu-mdr-ivdr/eu-technical-documentation ；NMPA 体外诊断试剂注册与备案管理规定（英文版 2024）— https://english.nmpa.gov.cn/2024-06/05/c_1049322.htm ；Cisema NMPA IVD 白皮书 — https://cisema.com/whitepapers/china-nmpa-registration-ivd-reagents-whitepaper

## 六、实证教训来源（条款的案例支撑）

条款 D6/M3/M8/M9/§7 特别警告等源自某内部 cfDNA 甲基化组织特异性分析库的治理实践：五轮结构重整史、wc -l 表头 off-by-one、目录遍历字典键覆盖污染、路径断裂致重跑假阳性、FTP 续传拼接损坏、nohup.out 无关进程残留等（细节不随公开仓库披露）。

## 七、通用质量、档案与数据合规（v3.1 补）

- ISO 9001 质量管理体系（记录控制）— https://www.iso.org/standards/popular/iso-9000-family
- ISO 15489-1 信息与文档—记录管理 — https://www.iso.org/standard/63142.html
- GDPR 全文（ELI 官方入口）— https://eur-lex.europa.eu/eli/reg/2016/679/oj
- 中国数据安全法、个人信息保护法（全国人大）— http://www.npc.gov.cn
- 会计档案管理办法（财政部、国家档案局令第 79 号）— 财政部官网 https://www.mof.gov.cn
- FAIR 数据原则 — https://www.go-fair.org/fair-principles/
- Semantic Versioning — https://semver.org
- DVC 数据版本控制 — https://dvc.org
