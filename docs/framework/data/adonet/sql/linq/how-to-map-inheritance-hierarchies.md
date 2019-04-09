---
title: 'Como: mapear hierarquias de herança'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: f75c7fe701c4a2fab1f993517828b38e5a26e2bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138080"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="2fc08-102">Como: mapear hierarquias de herança</span><span class="sxs-lookup"><span data-stu-id="2fc08-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="2fc08-103">Para implementar o mapeamento de herança em [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], você deve especificar atributos e propriedades de atributo na classe raiz da hierarquia de herança como descrito nas seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="2fc08-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="2fc08-104">Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear hierarquias de herança.</span><span class="sxs-lookup"><span data-stu-id="2fc08-104">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span> <span data-ttu-id="2fc08-105">Confira [Como Configurar a herança usando o Designer Relacional de Objetos](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="2fc08-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fc08-106">Qualquer atributo ou propriedade de especial são necessários nas subclasses.</span><span class="sxs-lookup"><span data-stu-id="2fc08-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="2fc08-107">Observe que as subclasses especialmente não têm o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2fc08-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="2fc08-108">Para mapear uma hierarquia de herança</span><span class="sxs-lookup"><span data-stu-id="2fc08-108">To map an inheritance hierarchy</span></span>  
  
1.  <span data-ttu-id="2fc08-109">Adicione o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> a classe raiz.</span><span class="sxs-lookup"><span data-stu-id="2fc08-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2.  <span data-ttu-id="2fc08-110">Também à classe raiz, adicione um atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> para cada classe na estrutura da hierarquia.</span><span class="sxs-lookup"><span data-stu-id="2fc08-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3.  <span data-ttu-id="2fc08-111">Para cada atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , defina uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .</span><span class="sxs-lookup"><span data-stu-id="2fc08-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="2fc08-112">Esta propriedade contém um valor que pareça na tabela de base de dados na coluna de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> para indicar que a classe ou da subclasse esta linha de dados pertencem.</span><span class="sxs-lookup"><span data-stu-id="2fc08-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4.  <span data-ttu-id="2fc08-113">Para cada atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , também adicionar uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> .</span><span class="sxs-lookup"><span data-stu-id="2fc08-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="2fc08-114">Esta propriedade contém um valor que especifica que a classe ou da subclasse o valor da chave significa.</span><span class="sxs-lookup"><span data-stu-id="2fc08-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5.  <span data-ttu-id="2fc08-115">Em apenas um dos atributos de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , adicione uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> .</span><span class="sxs-lookup"><span data-stu-id="2fc08-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="2fc08-116">Esta propriedade serve para designar uma *fallback* mapeamento quando o valor do discriminador da tabela de banco de dados não corresponde a nenhum <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> valor nos mapeamentos de herança.</span><span class="sxs-lookup"><span data-stu-id="2fc08-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6.  <span data-ttu-id="2fc08-117">Adicione uma propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> para um atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2fc08-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="2fc08-118">Esta propriedade significa que esta é a coluna que contém o valor de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .</span><span class="sxs-lookup"><span data-stu-id="2fc08-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fc08-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc08-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fc08-120">Se você estiver usando o Visual Studio, você pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para configurar a herança.</span><span class="sxs-lookup"><span data-stu-id="2fc08-120">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to configure inheritance.</span></span> <span data-ttu-id="2fc08-121">Confira [Como Configurar a herança usando o Designer Relacional de Objetos](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="2fc08-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="2fc08-122">No exemplo de código, `Vehicle` é definido como a classe raiz, e as etapas anteriores foram implementadas para descrever a hierarquia para [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2fc08-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2fc08-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc08-123">See also</span></span>

- [<span data-ttu-id="2fc08-124">Suporte à herança</span><span class="sxs-lookup"><span data-stu-id="2fc08-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [<span data-ttu-id="2fc08-125">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="2fc08-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
