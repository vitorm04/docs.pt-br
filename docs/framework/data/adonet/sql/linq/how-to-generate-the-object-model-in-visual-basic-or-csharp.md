---
title: Como gerar o modelo de objeto em Visual Basic ou C#
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 7d2c0600534c93f5884eec48a4bdaa3ce99945e9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002807"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Como gerar o modelo de objeto em Visual Basic ou C\#
No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], um modelo de objeto em sua própria linguagem de programação é mapeado para um banco de dados relacional. Duas ferramentas estão disponíveis para gerar automaticamente um Visual Basic ou C# modelo a partir dos metadados de um banco de dados existente.  
  
- Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para gerar um modelo de objeto. O o/R Designer fornece uma rica interface de usuário para ajudá-lo a gerar um modelo de objeto de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Para obter mais informações, consulte [Ferramentas do LINQ to SQL no Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- A ferramenta de linha de comando SQLMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Se você não tiver um banco de dados existente e não quiser criar um a partir de um modelo de objeto, poderá criar seu modelo de objeto usando o editor de códigos e <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Para obter mais informações, consulte [como criar dinamicamente um banco de dados](how-to-dynamically-create-a-database.md).  
  
 A documentação do o/R Designer fornece exemplos de como gerar um modelo de Visual Basic C# ou de objeto usando o o/r designer. As informações a seguir fornecem exemplos de como usar a ferramenta de linha de comando SqlMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 A linha de comando SqlMetal mostrada no exemplo a seguir produz Visual Basic código como o modelo de objeto baseado em atributo do banco de dados de exemplo Northwind. Os procedimentos armazenados e funções são renderizados também.  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 A linha de comando SQLMetal mostrada no exemplo a seguir gera código C# como o modelo de objeto baseado em atributos de banco de dados de exemplo Northwind. Os procedimentos armazenados e funções também são processados, e os nomes de tabela são automaticamente pluralizados.  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação](programming-guide.md)
- [O modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
- [Aprendendo com explicações passo a passo](learning-by-walkthroughs.md)
- [Como personalizar classes de entidade usando o Editor de código](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mapeamento baseado em atributos](attribute-based-mapping.md)
- [SqlMetal.exe (Ferramenta de Geração de Código)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Mapeamento Externo](external-mapping.md)
- [Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)
- [Criando o modelo de objeto](creating-the-object-model.md)
