---
title: 'Como: o chamar funções definidas em consultas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 575c7cff64608257646bde0ef08abe4c0096e477
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761643"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Como: o chamar funções definidas em consultas
Este tópico descreve como chamar funções que são definidas no modelo conceitual de dentro das consultas de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .  
  
 O procedimento a seguir fornece um contorno de alto nível para chamar uma função do definida em uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] . O exemplo a seguir fornece mais detalhes sobre as etapas no procedimento. O procedimento presume que você definiu uma função no modelo conceitual. Para obter mais informações, consulte [como: definir funções de personalizados no modelo conceitual](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Para chamar uma função definida no modelo conceitual  
  
1.  Adicione um método do Common Language Runtime (CLR) ao seu aplicativo que mapeia função definida no modelo conceitual. Para mapear o método, você deve aplicar <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> para o método. Observe que os parâmetros de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> e de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de atributo é o nome do espaço do modelo conceitual e o nome da função no modelo conceitual respectivamente. A resolução de nomes de função para LINQ diferencia maiúsculas de minúsculas.  
  
2.  Chamar a função em uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como chamar uma função que é definida no modelo conceitual de uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] . O exemplo usa o modelo de escola. Para obter informações sobre o modelo de escola, consulte [criando o banco de dados de exemplo School](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) e [gerando o EDMX escola arquivo](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 A função a seguir o modelo conceitual retorna o número de anos como um instrutor foi contratado. Para obter informações sobre como adicionar a função a um modelo conceitual, consulte [como: definir funções de personalizados no modelo conceitual](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
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
 [Visão geral do arquivo. edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Chamando funções em consultas LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Como chamar funções definidas por modelo como métodos de objeto](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
