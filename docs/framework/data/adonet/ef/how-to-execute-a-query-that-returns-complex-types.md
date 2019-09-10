---
title: 'Como: executar uma consulta que retorna tipos complexos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854644"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Como: executar uma consulta que retorna tipos complexos
Este tópico mostra como executar uma consulta de [!INCLUDE[esql](../../../../../includes/esql-md.md)] que retorna os objetos do tipo de entidade que contêm uma propriedade de um tipo complexo.  
  
### <a name="to-run-the-code-in-this-example"></a>Para executar o código nesse exemplo  
  
1. Adicione o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configure seu projeto para usar o Entity Framework. Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.  
  
2. Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Clique duas vezes no arquivo. edmx para exibir o modelo na [janela Navegador de modelos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) da Entity designer. Na superfície Entity designer, selecione as propriedades `Email` e `Phone` do tipo de `Contact` entidade, clique com o botão direito do mouse e selecione **refatorar em novo tipo complexo**.  
  
4. Um novo tipo complexo com as propriedades `Email` e `Phone` selecionadas é adicionado ao **navegador de modelo**. O tipo complexo recebe um nome padrão: renomeie o tipo `EmailPhone` para na janela **Propriedades** . Além disso, uma nova propriedade de `ComplexProperty` é adicionada ao tipo de entidade de `Contact` . Renomear a propriedade a `EmailPhoneComplexType.`  
  
     Para obter informações sobre como criar e modificar tipos complexos usando o assistente de modelo de dados de entidade [, consulte Como: Refatore as propriedades existentes em uma propriedade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) de tipo complexo e [como: Criar e modificar tipos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))complexos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa uma consulta que retorna uma coleção de `Contact` objetos e exibe duas propriedades `Contact` dos objetos: `ContactID` e os valores do `EmailPhoneComplexType` tipo complexo.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
