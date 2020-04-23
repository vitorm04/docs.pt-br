---
title: Diretiva x:Member
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071468"
---
# <a name="xmember-directive"></a><span data-ttu-id="82da4-102">Diretiva x:Member</span><span class="sxs-lookup"><span data-stu-id="82da4-102">x:Member Directive</span></span>
<span data-ttu-id="82da4-103">Declara um membro XAML na marcação.</span><span class="sxs-lookup"><span data-stu-id="82da4-103">Declares a XAML member in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="82da4-104">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="82da4-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="82da4-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="82da4-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="82da4-106">Nome da classe de apoio ou classe parcial para a produção xaml.</span><span class="sxs-lookup"><span data-stu-id="82da4-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`memberName`|<span data-ttu-id="82da4-107">Nome do membro da propriedade que está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="82da4-107">Member name of the property being defined.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82da4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="82da4-108">Remarks</span></span>

<span data-ttu-id="82da4-109">Na implementação do .NET XAML Services, .</span><span class="sxs-lookup"><span data-stu-id="82da4-109">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="82da4-110">`x:Member`não tem um tipo direto de apoio, <xref:System.Windows.Markup.MemberDefinition> mas é suportado pela classe.</span><span class="sxs-lookup"><span data-stu-id="82da4-110">`x:Member` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.MemberDefinition> class.</span></span> <span data-ttu-id="82da4-111">Em um fluxo de nó `x:Member` XAML, um `Member`elemento é representado como um membro chamado , a partir do espaço de nome XAML.</span><span class="sxs-lookup"><span data-stu-id="82da4-111">In a XAML node stream, an `x:Member` element is represented as a member named `Member`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="82da4-112">O `Member` membro possui atributos declarados pela marcação.</span><span class="sxs-lookup"><span data-stu-id="82da4-112">The member `Member` holds attributes as declared by markup.</span></span>

<span data-ttu-id="82da4-113">O significado `Name` `Type` de e não são atribuídos ao nível de Serviços .NET XAML.</span><span class="sxs-lookup"><span data-stu-id="82da4-113">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="82da4-114">Eles são armazenados no fluxo inicial do nó XAML como valores de seqüência, a serem interpretados posteriormente sob as regras que podem ser impostas por estruturas específicas.</span><span class="sxs-lookup"><span data-stu-id="82da4-114">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="82da4-115">O significado pode se alinhar a um nome XAML e ao significado do tipo XAML, ou pode ser válido apenas em um sistema de tipo de backup, dependendo da implementação.</span><span class="sxs-lookup"><span data-stu-id="82da4-115">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="82da4-116">Para apoiar um `x:Members` uso prático de como um meio de especificar definições de membros na marcação, os membros devem ser associados a uma classe que pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="82da4-116">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="82da4-117">O modelo pretendido `x:Members` é que existe como um `x:Class`membro de um tipo que especifica um .</span><span class="sxs-lookup"><span data-stu-id="82da4-117">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="82da4-118">No entanto, o mecanismo para associar tipos e membros ou para produzir definições dinâmicas de membros não é suportado no nível de Serviços .NET XAML.</span><span class="sxs-lookup"><span data-stu-id="82da4-118">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="82da4-119">Isso é deixado para estruturas individuais que têm modelos de aplicativos que suportam definições de membros a partir de XAML.</span><span class="sxs-lookup"><span data-stu-id="82da4-119">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="82da4-120">Normalmente, o MSBUILD constrói ações que compilam o XAML e o integram com o código-atrás ou produzem conjuntos puros de XAML para suportar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="82da4-120">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="82da4-121">x:Propriedade para Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="82da4-121">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="82da4-122">Para o Windows `x:Property` Workflow Foundation, define os membros de uma atividade personalizada composta inteiramente em XAML, ou XAML – membros dinâmicos definidos para um designer de atividades com código atrás.</span><span class="sxs-lookup"><span data-stu-id="82da4-122">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="82da4-123">`x:Class`também deve ser especificado no elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="82da4-123">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="82da4-124">Isso não é um requisito no nível de Serviços XAML .NET, mas se torna um requisito quando a produção XAML é carregada pelas ações de compilação do MSBUILD que suportam atividades personalizadas e o Windows Workflow Foundation XAML em geral.</span><span class="sxs-lookup"><span data-stu-id="82da4-124">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="82da4-125">O Windows Workflow Foundation não usa o nome do tipo `x:Property` `Type` XAML puro como seu valor pretendido para o atributo e, em vez disso, usa uma convenção que não está documentada aqui.</span><span class="sxs-lookup"><span data-stu-id="82da4-125">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="82da4-126">Para obter mais informações, consulte [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="82da4-126">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
