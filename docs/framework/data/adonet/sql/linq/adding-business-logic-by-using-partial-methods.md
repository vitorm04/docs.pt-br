---
title: Adicionando a lógica comercial usando métodos parciais
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 9ad3329c621b8bf8eaa0fd5f986ac7e8cff97d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156154"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="efbdd-102">Adicionando a lógica comercial usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="efbdd-102">Adding Business Logic By Using Partial Methods</span></span>

<span data-ttu-id="efbdd-103">Você pode personalizar o Visual Basic e o código gerado em C# em seus [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projetos usando *métodos parciais*.</span><span class="sxs-lookup"><span data-stu-id="efbdd-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="efbdd-104">O código que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gerencia define assinaturas como uma parte de um método parcial.</span><span class="sxs-lookup"><span data-stu-id="efbdd-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="efbdd-105">Se você deseja implementar o método, você pode adicionar seu próprio método parcial.</span><span class="sxs-lookup"><span data-stu-id="efbdd-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="efbdd-106">Se você não adiciona sua própria implementação, o compilador descarta a assinatura parcial de métodos e chama os métodos padrão em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efbdd-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efbdd-107">Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para adicionar validação e outras personalizações a classes de entidade.</span><span class="sxs-lookup"><span data-stu-id="efbdd-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="efbdd-108">Por exemplo, o mapeamento padrão para a classe de `Customer` na base de dados de exemplo Northwind inclui o seguinte método parcial:</span><span class="sxs-lookup"><span data-stu-id="efbdd-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="efbdd-109">Você pode implementar seu próprio método adicionando o código como o seguinte a sua própria classe parcial de `Customer` :</span><span class="sxs-lookup"><span data-stu-id="efbdd-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="efbdd-110">Essa abordagem é normalmente usada no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir os métodos padrão para `Insert` , `Update` , `Delete` e para validar Propriedades durante eventos do ciclo de vida do objeto.</span><span class="sxs-lookup"><span data-stu-id="efbdd-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="efbdd-111">Para obter mais informações, consulte [partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) ou [Partial (Method) (referência c#)](../../../../../csharp/language-reference/keywords/partial-method.md) (c#).</span><span class="sxs-lookup"><span data-stu-id="efbdd-111">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="efbdd-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="efbdd-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="efbdd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="efbdd-113">Description</span></span>  

 <span data-ttu-id="efbdd-114">O exemplo a seguir mostra como `ExampleClass` primeiro pode ser definido por uma ferramenta de geração como SQLMetal e em seguida, como você pode implementar apenas um dos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="efbdd-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="efbdd-115">Código</span><span class="sxs-lookup"><span data-stu-id="efbdd-115">Code</span></span>  

 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="efbdd-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="efbdd-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="efbdd-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="efbdd-117">Description</span></span>  

 <span data-ttu-id="efbdd-118">O exemplo a seguir usa a relação entre `Shipper` e entidades de `Order` .</span><span class="sxs-lookup"><span data-stu-id="efbdd-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="efbdd-119">Observe entre os métodos métodos parciais, `InsertShipper` e `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="efbdd-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="efbdd-120">Esses métodos substituem os métodos parciais padrão fornecidos pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapeamento.</span><span class="sxs-lookup"><span data-stu-id="efbdd-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="efbdd-121">Código</span><span class="sxs-lookup"><span data-stu-id="efbdd-121">Code</span></span>  

 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="efbdd-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="efbdd-122">See also</span></span>

- [<span data-ttu-id="efbdd-123">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="efbdd-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="efbdd-124">Personalizando a inserção, atualiazação, e as operações de exclusão</span><span class="sxs-lookup"><span data-stu-id="efbdd-124">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
