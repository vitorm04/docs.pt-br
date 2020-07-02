---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614418"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a><span data-ttu-id="c4fbe-101">WPF alterando uma chave primária ao exibir dados ADO em um cenário de detalhes/mestre</span><span class="sxs-lookup"><span data-stu-id="c4fbe-101">WPF Changing a primary key when displaying ADO data in a Master/Detail scenario</span></span>

#### <a name="details"></a><span data-ttu-id="c4fbe-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c4fbe-102">Details</span></span>

<span data-ttu-id="c4fbe-103">Suponha que você tenha uma coleção ADO de itens do tipo `Order`, com uma relação denominada &quot;OrderDetails&quot;, relacionando-a a uma coleção de itens do tipo `Detail` por meio da chave primária &quot;OrderID&quot;.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-103">Suppose you have an ADO collection of items of type `Order`, with a relation named &quot;OrderDetails&quot; relating it to a collection of items of type `Detail` via the primary key &quot;OrderID&quot;.</span></span> <span data-ttu-id="c4fbe-104">No seu aplicativo WPF, você pode vincular um controle de lista aos detalhes de determinado pedido:</span><span class="sxs-lookup"><span data-stu-id="c4fbe-104">In your WPF app, you can bind a list control to the details for a given order:</span></span>

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

<span data-ttu-id="c4fbe-105">em que o DataContext é um `Order`.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-105">where the DataContext is an `Order`.</span></span> <span data-ttu-id="c4fbe-106">O WPF Obtém o valor da `OrderDetails` Propriedade – uma coleção D de todos os `Detail` itens cujo `OrderID` corresponde ao `OrderID` do item mestre.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-106">WPF gets the value of the `OrderDetails` property - a collection D of all the `Detail` items whose `OrderID` matches the `OrderID` of the master item.</span></span> <span data-ttu-id="c4fbe-107">A alteração de comportamento surge quando você altera a chave primária `OrderID` do item mestre.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-107">The behavior change arises when you change the primary key `OrderID` of the master item.</span></span> <span data-ttu-id="c4fbe-108">O ADO altera automaticamente a `OrderID` de cada um dos registros afetados na coleção Detalhes (ou seja, os que foram copiados na coleção D).</span><span class="sxs-lookup"><span data-stu-id="c4fbe-108">ADO automatically changes the `OrderID` of each of the affected records in the Details collection (namely the ones copied into collection D).</span></span>  <span data-ttu-id="c4fbe-109">Mas o que acontece com D?</span><span class="sxs-lookup"><span data-stu-id="c4fbe-109">But what happens to D?</span></span>

- <span data-ttu-id="c4fbe-110">Comportamento antigo: a coleção D está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-110">Old behavior: Collection D is cleared.</span></span> <span data-ttu-id="c4fbe-111">O item mestre *não* gera uma notificação de alteração para a propriedade `OrderDetails`.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-111">The master item does *not* raise a change notification for property `OrderDetails`.</span></span> <span data-ttu-id="c4fbe-112">O ListBox continua a usar a coleção D, que agora está vazia.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-112">The ListBox continues to use collection D, which is now empty.</span></span>
- <span data-ttu-id="c4fbe-113">Novo comportamento: a coleção D fica inalterada.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-113">New behavior:  Collection D is unchanged.</span></span> <span data-ttu-id="c4fbe-114">Cada um dos seus itens gera uma notificação de alteração para a propriedade `OrderID`.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-114">Each of its items raises a change notification for the `OrderID` property.</span></span> <span data-ttu-id="c4fbe-115">O ListBox continua a usar a coleção D e exibe os detalhes com a nova `OrderID`.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-115">The ListBox continues to use collection D, and displays the details with the new `OrderID`.</span></span> <span data-ttu-id="c4fbe-116">O WPF implementa o novo comportamento criando a coleção D de uma maneira diferente: chamando o método ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> com o argumento `followParent` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-116">WPF implements the new behavior by creating collection D in a different way:  by calling the ADO method <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> with the `followParent` argument set to `true`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c4fbe-117">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c4fbe-117">Suggestion</span></span>

<span data-ttu-id="c4fbe-118">Um aplicativo obtém o novo comportamento usando o comutador AppContext a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-118">An app gets the new behavior by using the following AppContext switch.</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

<span data-ttu-id="c4fbe-119">O padrão do comutador é `true` (comportamento antigo) para aplicativos direcionados para o .NET 4.7.1 ou anterior e `false` (novo comportamento) para aplicativos direcionados para o .NET 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="c4fbe-119">The switch defaults to `true` (old behavior) for apps that target .NET 4.7.1 or below, and to `false` (new behavior) for apps that target .NET 4.7.2 or above.</span></span>

| <span data-ttu-id="c4fbe-120">Name</span><span class="sxs-lookup"><span data-stu-id="c4fbe-120">Name</span></span>    | <span data-ttu-id="c4fbe-121">Valor</span><span class="sxs-lookup"><span data-stu-id="c4fbe-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c4fbe-122">Escopo</span><span class="sxs-lookup"><span data-stu-id="c4fbe-122">Scope</span></span>   | <span data-ttu-id="c4fbe-123">Secundária</span><span class="sxs-lookup"><span data-stu-id="c4fbe-123">Minor</span></span>       |
| <span data-ttu-id="c4fbe-124">Versão</span><span class="sxs-lookup"><span data-stu-id="c4fbe-124">Version</span></span> | <span data-ttu-id="c4fbe-125">4.7.2</span><span class="sxs-lookup"><span data-stu-id="c4fbe-125">4.7.2</span></span>       |
| <span data-ttu-id="c4fbe-126">Type</span><span class="sxs-lookup"><span data-stu-id="c4fbe-126">Type</span></span>    | <span data-ttu-id="c4fbe-127">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="c4fbe-127">Retargeting</span></span> |
