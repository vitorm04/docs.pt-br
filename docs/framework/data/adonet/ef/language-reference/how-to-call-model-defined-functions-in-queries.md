---
title: 'Como: Chamar funções definidas por modelo em consultas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 2fe0360a0548bddb0ebba566eca0d121c9ec9160
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300613"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Como: Chamar funções definidas por modelo em consultas
Este tópico descreve como chamar funções que são definidas no modelo conceitual de dentro das consultas de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .  
  
 O procedimento a seguir fornece um contorno de alto nível para chamar uma função do definida em uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] . O exemplo a seguir fornece mais detalhes sobre as etapas no procedimento. O procedimento presume que você definiu uma função no modelo conceitual. Para obter mais informações, confira [Como: Definir funções personalizadas no modelo conceitual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Para chamar uma função definida no modelo conceitual  
  
1. Adicione um método do Common Language Runtime (CLR) ao seu aplicativo que mapeia função definida no modelo conceitual. Para mapear o método, você deve aplicar <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> para o método. Observe que os parâmetros de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> e de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de atributo é o nome do espaço do modelo conceitual e o nome da função no modelo conceitual respectivamente. A resolução de nomes de função para LINQ diferencia maiúsculas de minúsculas.  
  
2. Chamar a função em uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como chamar uma função que é definida no modelo conceitual de uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] . O exemplo usa o modelo de escola. Para obter informações sobre o modelo de escola, consulte [criando o banco de dados de exemplo School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) e [gerando a. edmx de escola arquivo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 A função a seguir o modelo conceitual retorna o número de anos como um instrutor foi contratado. Para obter informações sobre como adicionar a função a um modelo conceitual, consulte [como: Definir funções personalizadas no modelo conceitual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Exemplo  
 Em seguida, adicione o seguinte método ao seu aplicativo e usa <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> para mapear-lo à função de modelo conceitual:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Exemplo  
 Agora você pode chamar a função do modelo conceitual de uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] . O código a seguir chama o método para exibir todos os instrutores que foram contratados mais de dez anos há:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Chamando funções em consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Como: Chamar funções definidas por modelo como métodos de objeto](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
