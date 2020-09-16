---
title: Diretiva x:Member
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: 1c5b26b405e574290af54b29b22fb5e19e4b6b95
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548241"
---
# <a name="xmember-directive"></a><span data-ttu-id="30304-102">Diretiva x:Member</span><span class="sxs-lookup"><span data-stu-id="30304-102">x:Member Directive</span></span>
<span data-ttu-id="30304-103">Declara um membro XAML na marcação.</span><span class="sxs-lookup"><span data-stu-id="30304-103">Declares a XAML member in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="30304-104">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="30304-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="30304-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="30304-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="30304-106">Nome da classe de backup ou da classe parcial para a produção XAML.</span><span class="sxs-lookup"><span data-stu-id="30304-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`memberName`|<span data-ttu-id="30304-107">Nome do membro da propriedade que está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="30304-107">Member name of the property being defined.</span></span>|

## <a name="remarks"></a><span data-ttu-id="30304-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="30304-108">Remarks</span></span>

<span data-ttu-id="30304-109">Na implementação de serviços XAML .NET,.</span><span class="sxs-lookup"><span data-stu-id="30304-109">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="30304-110">`x:Member` Não tem um tipo direto de backup, mas é suportado pela <xref:System.Windows.Markup.MemberDefinition> classe.</span><span class="sxs-lookup"><span data-stu-id="30304-110">`x:Member` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.MemberDefinition> class.</span></span> <span data-ttu-id="30304-111">Em um fluxo de nó XAML, um `x:Member` elemento é representado como um membro chamado `Member` , do namespace XAML da linguagem XAML.</span><span class="sxs-lookup"><span data-stu-id="30304-111">In a XAML node stream, an `x:Member` element is represented as a member named `Member`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="30304-112">O membro `Member` mantém atributos como declarados pela marcação.</span><span class="sxs-lookup"><span data-stu-id="30304-112">The member `Member` holds attributes as declared by markup.</span></span>

<span data-ttu-id="30304-113">O significado de `Name` e `Type` não são atribuídos no nível de serviços XAML .net.</span><span class="sxs-lookup"><span data-stu-id="30304-113">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="30304-114">Eles são armazenados no fluxo do nó XAML inicial como valores de cadeia de caracteres, para serem interpretados posteriormente sob as regras que podem ser impostas por estruturas específicas.</span><span class="sxs-lookup"><span data-stu-id="30304-114">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="30304-115">O significado pode ser alinhado a um nome XAML e ao tipo XAML significado, ou só pode ser válido em um sistema de tipo de apoio, dependendo da implementação.</span><span class="sxs-lookup"><span data-stu-id="30304-115">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="30304-116">Para dar suporte a um uso prático de `x:Members` como um meio de especificar definições de membro na marcação, os membros devem ser associados a uma classe que pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="30304-116">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="30304-117">O modelo pretendido é que `x:Members` existe como um membro de um tipo que especifica um `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="30304-117">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="30304-118">No entanto, o mecanismo para associar tipos e membros ou para produzir definições de membros dinâmicos não tem suporte no nível de serviços XAML .NET.</span><span class="sxs-lookup"><span data-stu-id="30304-118">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="30304-119">Isso é deixado para estruturas individuais que têm modelos de aplicativo que dão suporte a definições de membro do XAML.</span><span class="sxs-lookup"><span data-stu-id="30304-119">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="30304-120">Normalmente, as ações de compilação do MSBUILD que marcam a marcação XAML e a integram com code-behind ou geram assemblies puros de XAML são necessários para dar suporte a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="30304-120">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="30304-121">x:Property para Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="30304-121">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="30304-122">Por Windows Workflow Foundation, `x:Property` define os membros de uma atividade personalizada composta inteiramente em XAML ou membros dinâmicos definidos pelo XAML para um designer de atividade com code-behind.</span><span class="sxs-lookup"><span data-stu-id="30304-122">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="30304-123">`x:Class` também deve ser especificado no elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="30304-123">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="30304-124">Isso não é um requisito no nível de serviços XAML .NET, mas se torna um requisito quando a produção XAML é carregada pelas ações de compilação do MSBUILD que dão suporte a atividades personalizadas e Windows Workflow Foundation XAML em geral.</span><span class="sxs-lookup"><span data-stu-id="30304-124">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="30304-125">Windows Workflow Foundation não usa o nome do tipo puro XAML como seu valor pretendido para o `x:Property` `Type` atributo e, em vez disso, usa uma convenção que não está documentada aqui.</span><span class="sxs-lookup"><span data-stu-id="30304-125">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="30304-126">Para obter mais informações, consulte [criação de DynamicActivity](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="30304-126">For more information, see [DynamicActivity Creation](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
