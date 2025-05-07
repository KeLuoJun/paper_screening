# 基于多模态的竞赛论文自动筛选系统

## 目录
- [依赖项](#环境要求)
- [使用方法](#使用方法)
- [程序功能](#程序功能)
- [注意事项](#Tips)


## 环境要求
### 依赖安装
请确保先安装依赖环境。
```bash
pip install -r requirements.txt
```
### 模型下载
- Mineru模型的安装参考[Mineru](https://github.com/Mineru/Mineru)。
- bert-base-chinese的下载链接[bert-base-chinese](https://huggingface.co/google-bert/bert-base-chinese)。
- resnet50-06765b.pth的下载链接[resnet50-0676ba61.pth](https://download.pytorch.org/models/resnet50-0676ba61.pth)


## 使用方法

1. 将附件数据（附件1、附件2、附件3）放入`data`目录下。
- 附件1：论文提交队伍信息（.csv）
- 附件2：论文写作主题 (.pdf)
- 附件3：论文PDF合集

2. 使用`pdf_transform.ipynb`将附件3的PDF文件进行转换，放在`data/transform`目录下。


## 程序功能：
- `method1.ipynb`: 提取论文中的元数据（参赛队号、论文标题、论文总页数、论文总字数、摘要页数、摘要字数、目录页数、正文页数、正文字数	、正文中图片数、正文图片所占比例、正文表格数、正文独立公式数、正文段落数量、正文段落平均句子数、正文段落平均字数、参考文献数量、附录页数、附录代码行数），结果保存在result1.xlsx 中。
- `method2.ipynb`: 从所有论文中，筛选出包含参赛队信息的论文；通过提取特征，分析判断正文内容是否与论文写作主题无关；根据附件 2 中赛题的要求，识别出无实质内容的论文。将所有竞赛论文的判断结果保存在 result2.xlsx（其中 B，C，D 列的值为 0 或 1：0 表示“否”，1 表示“是”）。
- `method3.ipynb`: 定义并计算竞赛论文的重复率，将结果保存到文件 result3.xlsx 的相应工作表中。分析判断每篇竞赛论文中的图片、公式是否与其他论文中的图片、公式雷同，将雷同图片、公式所在页码及页内序号分别保存在 result3.xlsx（页码指 PDF 文件的页码，可能与论文的页码不一致）。
-  `method4.ipynb`: 针对图片占比过高的论文给出识别率更精准的相似性检测的模型(resnet50)，并重新计算所有论文的重复率，将结果保存在 result4.xlsx。


## Tips
建议安装Mineru的GPU版本，显著提高PDF转换效率。


