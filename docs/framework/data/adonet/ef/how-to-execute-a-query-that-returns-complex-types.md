---
title: 'Como: executar uma consulta que retorna tipos complexos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 01958637cedcd6d502d51e9f0821ff3a9faae840
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545318"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Como: executar uma consulta que retorna tipos complexos
Este tópico mostra como executar uma consulta de [!INCLUDE[esql](../../../../../includes/esql-md.md)] que retorna os objetos do tipo de entidade que contêm uma propriedade de um tipo complexo.  
  
### <a name="to-run-the-code-in-this-example"></a>Para executar o código nesse exemplo  
  
1. Adicione o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configure seu projeto para usar o Entity Framework. Para obter mais informações, consulte [como: usar o assistente de modelo de dados de entidade](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Clique duas vezes no arquivo. edmx para exibir o modelo na [janela Navegador de modelos](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) da Entity designer. Na superfície Entity Designer, selecione as `Email` Propriedades e `Phone` do tipo de `Contact` entidade, clique com o botão direito do mouse e selecione **refatorar em novo tipo complexo**.  
  
4. Um novo tipo complexo com as `Email` Propriedades e selecionadas `Phone` é adicionado ao **navegador de modelo**. O tipo complexo recebe um nome padrão: renomeie o tipo para `EmailPhone` na janela **Propriedades** . Além disso, uma nova propriedade de `ComplexProperty` é adicionada ao tipo de entidade de `Contact` . Renomear a propriedade a `EmailPhoneComplexType.`  
  
     Para obter informações sobre como criar e modificar tipos complexos usando o assistente de Modelo de Dados de Entidade, consulte [como: refatorar as propriedades existentes em uma propriedade de tipo complexo](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) e [como criar e modificar tipos complexos](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa uma consulta que retorna uma coleção de `Contact` objetos e exibe duas propriedades dos `Contact` objetos: `ContactID` e os valores do `EmailPhoneComplexType` tipo complexo.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
