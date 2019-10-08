---
title: 'Como: gerar código personalizado modificando um arquivo DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 6619f4b8c0a47b36a0b84fa21bab4109d26ef895
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002950"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Como: gerar código personalizado modificando um arquivo DBML
Você pode gerar Visual Basic ou C# código-fonte de um arquivo de metadados de linguagem de marcação de banco de dados (. dbml). Essa abordagem fornece uma oportunidade para personalizar o arquivo .dbml padrão antes de você gerar o código de mapeamento do aplicativo. Esse é um recurso avançado.  
  
 As etapas nesse processo são as seguintes:  
  
1. Gere um arquivo .dbml.  
  
2. Use um editor para modificar o arquivo .dbml. Observe que o arquivo. dbml deve validar em relação ao arquivo de definição de esquema (. xsd) para arquivos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. dbml. Para obter mais informações, consulte [geração de código em LINQ to SQL](code-generation-in-linq-to-sql.md).  
  
3. Gere o Visual Basic ou C# o código-fonte.  
  
 Os exemplos a seguir usam a ferramenta de linha de comando SQLMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir gera um arquivo .dbml do banco de dados de exemplo Northwind. Como a origem para os metadados de banco de dados, você pode usar o nome do banco de dados ou o nome do arquivo .mdf.  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir gera Visual Basic C# ou arquivo de código-fonte de um arquivo. dbml.  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Consulte também

- [Geração de código em LINQ to SQL](code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (Ferramenta de Geração de Código)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Criando o modelo de objeto](creating-the-object-model.md)
