---
title: Diretiva x:Subclass
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071363"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="74851-102">Diretiva x:Subclass</span><span class="sxs-lookup"><span data-stu-id="74851-102">x:Subclass Directive</span></span>

<span data-ttu-id="74851-103">Modifica o comportamento de compilação `x:Class` de marcação XAML quando também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="74851-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="74851-104">Em vez de criar uma `x:Class`classe parcial `x:Class` baseada em , o fornecido é criado como uma classe intermediária, `x:Class`e então espera-se que sua classe derivada fornecida seja baseada em .</span><span class="sxs-lookup"><span data-stu-id="74851-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="74851-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="74851-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="74851-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="74851-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="74851-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="74851-107">Optional.</span></span> <span data-ttu-id="74851-108">Especifica um namespace CLR `classname`que contenha .</span><span class="sxs-lookup"><span data-stu-id="74851-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="74851-109">Se `namespace` for especificado, um dot `namespace` (.) separa e `classname`.</span><span class="sxs-lookup"><span data-stu-id="74851-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="74851-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="74851-110">Required.</span></span> <span data-ttu-id="74851-111">Especifica o nome CLR da classe parcial que conecta o XAML carregado e o seu código-traseiro para esse XAML.</span><span class="sxs-lookup"><span data-stu-id="74851-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="74851-112">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="74851-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="74851-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="74851-113">Optional.</span></span> <span data-ttu-id="74851-114">Pode ser `namespace` diferente de se cada namespace pode resolver o outro.</span><span class="sxs-lookup"><span data-stu-id="74851-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="74851-115">Especifica um namespace CLR `subclassName`que contenha .</span><span class="sxs-lookup"><span data-stu-id="74851-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="74851-116">Se `subclassName` for especificado, um dot `subclassNamespace` (.) separa e `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="74851-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="74851-117">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="74851-117">Required.</span></span> <span data-ttu-id="74851-118">Especifica o nome CLR da subclasse.</span><span class="sxs-lookup"><span data-stu-id="74851-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="74851-119">Dependências</span><span class="sxs-lookup"><span data-stu-id="74851-119">Dependencies</span></span>

<span data-ttu-id="74851-120">[x:Diretiva de classe](xclass-directive.md) também deve ser fornecida no mesmo objeto, e esse objeto deve ser o elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="74851-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="74851-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="74851-121">Remarks</span></span>

<span data-ttu-id="74851-122">`x:Subclass`o uso é destinado principalmente a idiomas que não suportam declarações parciais de classe.</span><span class="sxs-lookup"><span data-stu-id="74851-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="74851-123">A classe usada `x:Subclass` como não pode ser `x:Subclass` uma classe aninhada, e deve se referir ao objeto raiz conforme explicado na seção "Dependências".</span><span class="sxs-lookup"><span data-stu-id="74851-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="74851-124">Caso contrário, o `x:Subclass` significado conceitual de é indefinido por uma implementação de Serviços .NET XAML.</span><span class="sxs-lookup"><span data-stu-id="74851-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="74851-125">Isso porque o comportamento do .NET XAML Services não especifica o modelo de programação global pelo qual a marcação XAML e o código de backup estão conectados.</span><span class="sxs-lookup"><span data-stu-id="74851-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="74851-126">Implementações de outros `x:Class` conceitos `x:Subclass` relacionados e são realizadas por estruturas específicas que usam modelos de programação ou modelos de aplicativos para definir como conectar marcação XAML, marcação compilada e code-behind baseado em CLR.</span><span class="sxs-lookup"><span data-stu-id="74851-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="74851-127">Cada estrutura pode ter suas próprias ações de construção que permitem alguns dos comportamentos, ou componentes específicos que devem ser incluídos no ambiente de construção.</span><span class="sxs-lookup"><span data-stu-id="74851-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="74851-128">Dentro de uma estrutura, as ações de construção também podem variar de acordo com a linguagem CLR específica que é usada para o code-behind.</span><span class="sxs-lookup"><span data-stu-id="74851-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="74851-129">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="74851-129">WPF Usage Notes</span></span>

<span data-ttu-id="74851-130">`x:Subclass`pode estar em uma raiz <xref:System.Windows.Application> de página ou na `x:Class`raiz na definição do aplicativo, que já tem .</span><span class="sxs-lookup"><span data-stu-id="74851-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="74851-131">Declarar `x:Subclass` em qualquer elemento que não seja uma página ou `x:Class` raiz de aplicativo, ou especiá-lo onde não existe, causa um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="74851-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="74851-132">Criar classes derivadas que funcionem corretamente para o `x:Subclass` cenário é bastante complexo.</span><span class="sxs-lookup"><span data-stu-id="74851-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="74851-133">Você pode precisar examinar os arquivos intermediários (os arquivos .g produzidos na pasta obj do seu projeto por compilação de marcação, com nomes que incorporam os nomes de arquivo .xaml).</span><span class="sxs-lookup"><span data-stu-id="74851-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="74851-134">Esses arquivos intermediários podem ajudá-lo a determinar a origem de certos construtos de programação nas classes parciais unidas no aplicativo compilado.</span><span class="sxs-lookup"><span data-stu-id="74851-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="74851-135">Os manipuladores de eventos na `internal override` `Friend Overrides` classe derivada devem ser (no Microsoft Visual Basic) a fim de substituir os stubs para os manipuladores como criados na classe intermediária durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="74851-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="74851-136">Caso contrário, as implementações de classe derivadas ocultam (sombra) a implementação da classe intermediária e os manipuladores de classe intermediária não são invocados.</span><span class="sxs-lookup"><span data-stu-id="74851-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="74851-137">Quando você `x:Class` define `x:Subclass`ambos e , você não precisa fornecer qualquer `x:Class`implementação para a classe que é referenciada por .</span><span class="sxs-lookup"><span data-stu-id="74851-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="74851-138">Você só precisa dar-lhe `x:Class` um nome através do atributo para que o compilador tenha alguma orientação para a classe que ele cria nos arquivos intermediários (o compilador não seleciona um nome padrão neste caso).</span><span class="sxs-lookup"><span data-stu-id="74851-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="74851-139">Você pode `x:Class` dar à classe uma implementação; no entanto, este não é `x:Class` `x:Subclass`o cenário típico para o uso de ambos e .</span><span class="sxs-lookup"><span data-stu-id="74851-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="74851-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="74851-140">See also</span></span>

- [<span data-ttu-id="74851-141">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="74851-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="74851-142">XAML e classes personalizadas para WPF</span><span class="sxs-lookup"><span data-stu-id="74851-142">XAML and Custom Classes for WPF</span></span>](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
