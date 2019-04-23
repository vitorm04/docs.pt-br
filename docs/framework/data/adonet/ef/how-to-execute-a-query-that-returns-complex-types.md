---
title: 'Como: executar uma consulta que retorna tipos complexos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: a428f54c3834ccdf6a0c7a5bfce8307172724524
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322882"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Como: executar uma consulta que retorna tipos complexos
Este tópico mostra como executar uma consulta de [!INCLUDE[esql](../../../../../includes/esql-md.md)] que retorna os objetos do tipo de entidade que contêm uma propriedade de um tipo complexo.  
  
### <a name="to-run-the-code-in-this-example"></a>Para executar o código nesse exemplo  
  
1. Adicione a [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Clique duas vezes o arquivo. edmx para exibir o modelo na [janela do navegador modelo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) do Designer de entidade. Na superfície do Designer de entidade, selecione a `Email` e `Phone` propriedades da `Contact` tipo de entidade, em seguida, clique com botão direito e selecione **Refactor no novo tipo complexo**.  
  
4. Um novo tipo complexo com selecionado `Email` e `Phone` propriedades é adicionado para o **Model Browser**. O tipo complexo recebe um nome padrão: renomeie o tipo para `EmailPhone` no **propriedades** janela. Além disso, uma nova propriedade de `ComplexProperty` é adicionada ao tipo de entidade de `Contact` . Renomear a propriedade a `EmailPhoneComplexType.`  
  
     Para obter informações sobre como criar e modificar tipos complexos usando o Assistente de modelo de dados de entidade, consulte [como: Refatorar as propriedades existentes em uma propriedade de tipo complexo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) e [como: Criar e modificar tipos complexos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa uma consulta que retorna uma coleção de `Contact` objetos e exibe duas propriedades do `Contact` objetos: `ContactID` e os valores da `EmailPhoneComplexType` tipo complexo.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
