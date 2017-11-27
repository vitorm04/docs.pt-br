---
title: "Adicionando a lógica comercial usando métodos parciais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f9cbaa156fd794a6f9faf44d8d980159f8ae520e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="56df6-102">Adicionando a lógica comercial usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="56df6-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="56df6-103">Você pode personalizar [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] e c# gerado código no seu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projetos usando *métodos parciais*.</span><span class="sxs-lookup"><span data-stu-id="56df6-103">You can customize [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="56df6-104">O código que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gerencia define assinaturas como uma parte de um método parcial.</span><span class="sxs-lookup"><span data-stu-id="56df6-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="56df6-105">Se você deseja implementar o método, você pode adicionar seu próprio método parcial.</span><span class="sxs-lookup"><span data-stu-id="56df6-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="56df6-106">Se você não adiciona sua própria implementação, o compilador descarta a assinatura parcial de métodos e chama os métodos padrão em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56df6-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56df6-107">Se você estiver usando [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], você pode usar [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para adicionar validação e outras personalizações a classes de entidade.</span><span class="sxs-lookup"><span data-stu-id="56df6-107">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="56df6-108">Por exemplo, o mapeamento padrão para a classe de `Customer` na base de dados de exemplo Northwind inclui o seguinte método parcial:</span><span class="sxs-lookup"><span data-stu-id="56df6-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="56df6-109">Você pode implementar seu próprio método adicionando o código como o seguinte a sua própria classe parcial de `Customer` :</span><span class="sxs-lookup"><span data-stu-id="56df6-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="56df6-110">Essa abordagem é usada normalmente em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir os métodos padrão para `Insert`, `Update`, `Delete`e para validar propriedades durante eventos de ciclo de vida do objeto.</span><span class="sxs-lookup"><span data-stu-id="56df6-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="56df6-111">Para obter mais informações, consulte [métodos parciais](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ou [partial (método) (referência de c#)](~/docs/csharp/language-reference/keywords/partial-method.md) (c#).</span><span class="sxs-lookup"><span data-stu-id="56df6-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56df6-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56df6-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="56df6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="56df6-113">Description</span></span>  
 <span data-ttu-id="56df6-114">O exemplo a seguir mostra como `ExampleClass` primeiro pode ser definido por uma ferramenta de geração como SQLMetal e em seguida, como você pode implementar apenas um dos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="56df6-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="56df6-115">Código</span><span class="sxs-lookup"><span data-stu-id="56df6-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="56df6-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56df6-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="56df6-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="56df6-117">Description</span></span>  
 <span data-ttu-id="56df6-118">O exemplo a seguir usa a relação entre `Shipper` e entidades de `Order` .</span><span class="sxs-lookup"><span data-stu-id="56df6-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="56df6-119">Observe entre os métodos métodos parciais, `InsertShipper` e `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="56df6-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="56df6-120">Esses métodos substituem os métodos parciais padrão fornecidos pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapeamento.</span><span class="sxs-lookup"><span data-stu-id="56df6-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="56df6-121">Código</span><span class="sxs-lookup"><span data-stu-id="56df6-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="56df6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56df6-122">See Also</span></span>  
 [<span data-ttu-id="56df6-123">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="56df6-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="56df6-124">Personalizando a inserção, atualização e exclusão de operações</span><span class="sxs-lookup"><span data-stu-id="56df6-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
