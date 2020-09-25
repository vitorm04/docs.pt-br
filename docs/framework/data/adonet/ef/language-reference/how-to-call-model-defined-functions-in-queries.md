---
title: 'Como: o chamar funções definidas em consultas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: b142ef820e964eaf5f1afed53a6b12a9344c7dda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189325"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="3ca85-102">Como: o chamar funções definidas em consultas</span><span class="sxs-lookup"><span data-stu-id="3ca85-102">How to: Call Model-Defined Functions in Queries</span></span>

<span data-ttu-id="3ca85-103">Este tópico descreve como chamar funções que são definidas no modelo conceitual de dentro de LINQ to Entities consultas.</span><span class="sxs-lookup"><span data-stu-id="3ca85-103">This topic describes how to call functions that are defined in the conceptual model from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="3ca85-104">O procedimento abaixo fornece uma estrutura de tópicos de alto nível para chamar uma função definida pelo modelo de dentro de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3ca85-104">The procedure below provides a high-level outline for calling a model-defined function from within a LINQ to Entities query.</span></span> <span data-ttu-id="3ca85-105">O exemplo a seguir fornece mais detalhes sobre as etapas no procedimento.</span><span class="sxs-lookup"><span data-stu-id="3ca85-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="3ca85-106">O procedimento presume que você definiu uma função no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="3ca85-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="3ca85-107">Para obter mais informações, consulte [como: definir funções personalizadas no modelo conceitual](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3ca85-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="3ca85-108">Para chamar uma função definida no modelo conceitual</span><span class="sxs-lookup"><span data-stu-id="3ca85-108">To call a function defined in the conceptual model</span></span>  
  
1. <span data-ttu-id="3ca85-109">Adicione um método do Common Language Runtime (CLR) ao seu aplicativo que mapeia função definida no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="3ca85-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="3ca85-110">Para mapear o método, você deve aplicar <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> para o método.</span><span class="sxs-lookup"><span data-stu-id="3ca85-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="3ca85-111">Observe que os parâmetros de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> e de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de atributo é o nome do espaço do modelo conceitual e o nome da função no modelo conceitual respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3ca85-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="3ca85-112">A resolução de nomes de função para LINQ diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="3ca85-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2. <span data-ttu-id="3ca85-113">Chame a função em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3ca85-113">Call the function in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ca85-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ca85-114">Example</span></span>  

 <span data-ttu-id="3ca85-115">O exemplo a seguir demonstra como chamar uma função que é definida no modelo conceitual de dentro de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3ca85-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a LINQ to Entities query.</span></span> <span data-ttu-id="3ca85-116">O exemplo usa o modelo de escola.</span><span class="sxs-lookup"><span data-stu-id="3ca85-116">The example uses the School model.</span></span> <span data-ttu-id="3ca85-117">Para obter informações sobre o modelo escolar, consulte [criando o banco de dados de exemplo da escola](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) e [gerando o arquivo School. edmx](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3ca85-117">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="3ca85-118">A função a seguir o modelo conceitual retorna o número de anos como um instrutor foi contratado.</span><span class="sxs-lookup"><span data-stu-id="3ca85-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="3ca85-119">Para obter informações sobre como adicionar a função a um modelo conceitual, consulte [como definir funções personalizadas no modelo conceitual](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3ca85-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="3ca85-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ca85-120">Example</span></span>  

 <span data-ttu-id="3ca85-121">Em seguida, adicione o seguinte método ao seu aplicativo e usa <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> para mapear-lo à função de modelo conceitual:</span><span class="sxs-lookup"><span data-stu-id="3ca85-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="3ca85-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ca85-122">Example</span></span>  

 <span data-ttu-id="3ca85-123">Agora você pode chamar a função de modelo conceitual de dentro de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3ca85-123">Now you can call the conceptual model function from within a LINQ to Entities query.</span></span> <span data-ttu-id="3ca85-124">O código a seguir chama o método para exibir todos os instrutores que foram contratados mais de dez anos há:</span><span class="sxs-lookup"><span data-stu-id="3ca85-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3ca85-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="3ca85-125">See also</span></span>

- <span data-ttu-id="3ca85-126">[Visão geral do arquivo. edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3ca85-126">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="3ca85-127">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3ca85-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="3ca85-128">Chamando funções em consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3ca85-128">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="3ca85-129">Como: o chamar funções definidas como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="3ca85-129">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)
