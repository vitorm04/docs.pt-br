---
title: 'Como: especificar quais membros são testados quanto a conflitos de simultaneidade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: de7109e0fed0eb7c1975ad7360a7588ef9b294ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793148"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="468dc-102">Como: especificar quais membros são testados quanto a conflitos de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="468dc-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="468dc-103">Aplique uma das três enums à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar quais membros devem ser incluídos nas verificações de atualização para a detecção de conflitos de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="468dc-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="468dc-104">A propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (mapeada em tempo de design) é usada junto com recursos de simultaneidade de tempo de execução em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="468dc-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="468dc-105">Para obter mais informações, [consulte simultaneidade otimista: Visão](optimistic-concurrency-overview.md)geral.</span><span class="sxs-lookup"><span data-stu-id="468dc-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="468dc-106">Os valores membro original são comparados com o estado atual de base de dados como nenhum membro é designado como `IsVersion=true`.</span><span class="sxs-lookup"><span data-stu-id="468dc-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="468dc-107">Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="468dc-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="468dc-108">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="468dc-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="468dc-109">Para usar sempre esse membro para detectar conflitos</span><span class="sxs-lookup"><span data-stu-id="468dc-109">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="468dc-110">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="468dc-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="468dc-111">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `Always`.</span><span class="sxs-lookup"><span data-stu-id="468dc-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="468dc-112">Para usar nunca esse membro para detectar conflitos</span><span class="sxs-lookup"><span data-stu-id="468dc-112">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="468dc-113">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="468dc-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="468dc-114">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `Never`.</span><span class="sxs-lookup"><span data-stu-id="468dc-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="468dc-115">Para usar este membro para detectar conflitos somente quando o aplicativo altere o valor do membro</span><span class="sxs-lookup"><span data-stu-id="468dc-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="468dc-116">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="468dc-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="468dc-117">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `WhenChanged`.</span><span class="sxs-lookup"><span data-stu-id="468dc-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="468dc-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="468dc-118">Example</span></span>  
 <span data-ttu-id="468dc-119">O exemplo a seguir especifica que os objetos de `HomePage` nunca devem ser testados durante verificações de atualização.</span><span class="sxs-lookup"><span data-stu-id="468dc-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="468dc-120">Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="468dc-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="468dc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="468dc-121">See also</span></span>

- [<span data-ttu-id="468dc-122">Como: Gerenciar conflitos de alterações</span><span class="sxs-lookup"><span data-stu-id="468dc-122">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="468dc-123">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="468dc-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
