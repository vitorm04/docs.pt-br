---
title: 'Como: gerar o modelo de objeto em Visual Basic ou em C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 07df915b5c826c7b82f2aaf16fcc22da0361d5f6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781917"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Como: Gerar o modelo de objeto em Visual Basic ou C\#
No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], um modelo de objeto em sua própria linguagem de programação é mapeado para um banco de dados relacional. Duas ferramentas estão disponíveis para gerar automaticamente um Visual Basic ou C# modelo a partir dos metadados de um banco de dados existente.  
  
- Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para gerar um modelo de objeto. O o/R Designer fornece uma rica interface do usuário para ajudá-lo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a gerar um modelo de objeto. Para obter mais informações, consulte [Ferramentas do LINQ to SQL no Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- A ferramenta de linha de comando SQLMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Se você não tiver um banco de dados existente e não quiser criar um a partir de um modelo de objeto, poderá criar seu modelo de objeto usando o editor de códigos e <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Para obter mais informações, confira [Como: Crie dinamicamente um banco](how-to-dynamically-create-a-database.md)de dados.  
  
 A documentação do o/R Designer fornece exemplos de como gerar um modelo de Visual Basic C# ou de objeto usando o o/r designer. As informações a seguir fornecem exemplos de como usar a ferramenta de linha de comando SqlMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemplo  
 A linha de comando SqlMetal mostrada no exemplo a seguir produz Visual Basic código como o modelo de objeto baseado em atributo do banco de dados de exemplo Northwind. Os procedimentos armazenados e funções são renderizados também.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Exemplo  
 A linha de comando SQLMetal mostrada no exemplo a seguir gera código C# como o modelo de objeto baseado em atributos de banco de dados de exemplo Northwind. Os procedimentos armazenados e funções também são processados, e os nomes de tabela são automaticamente pluralizados.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação](programming-guide.md)
- [O modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
- [Aprendendo com explicações passo a passo](learning-by-walkthroughs.md)
- [Como: Personalizar classes de entidade usando o editor de código](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mapeamento baseado em atributos](attribute-based-mapping.md)
- [SqlMetal.exe (Ferramenta de Geração de Código)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Mapeamento Externo](external-mapping.md)
- [Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)
- [Criando o modelo de objeto](creating-the-object-model.md)
