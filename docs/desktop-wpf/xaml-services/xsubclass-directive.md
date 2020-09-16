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
ms.openlocfilehash: b888ef73d1678fd37c984e4bb223f24e5b65d2cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540713"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="b9c5f-102">Diretiva x:Subclass</span><span class="sxs-lookup"><span data-stu-id="b9c5f-102">x:Subclass Directive</span></span>

<span data-ttu-id="b9c5f-103">Modifica o comportamento de compilação de marcação XAML quando `x:Class` também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="b9c5f-104">Em vez de criar uma classe parcial baseada em `x:Class` , a fornecida `x:Class` é criada como uma classe intermediária e, em seguida, a classe derivada fornecida deve se basear `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="b9c5f-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="b9c5f-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="b9c5f-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="b9c5f-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="b9c5f-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-107">Optional.</span></span> <span data-ttu-id="b9c5f-108">Especifica um namespace CLR que contém `classname` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="b9c5f-109">Se `namespace` for especificado, um ponto (.) separa `namespace` e `classname` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="b9c5f-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-110">Required.</span></span> <span data-ttu-id="b9c5f-111">Especifica o nome CLR da classe parcial que conecta o XAML carregado e seu code-behind para esse XAML.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="b9c5f-112">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="b9c5f-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-113">Optional.</span></span> <span data-ttu-id="b9c5f-114">Pode ser diferente de `namespace` se cada namespace puder resolver o outro.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="b9c5f-115">Especifica um namespace CLR que contém `subclassName` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="b9c5f-116">Se `subclassName` for especificado, um ponto (.) separa `subclassNamespace` e `subclassName` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="b9c5f-117">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-117">Required.</span></span> <span data-ttu-id="b9c5f-118">Especifica o nome CLR da subclasse.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="b9c5f-119">Dependências</span><span class="sxs-lookup"><span data-stu-id="b9c5f-119">Dependencies</span></span>

<span data-ttu-id="b9c5f-120">a [diretiva x:Class](xclass-directive.md) também deve ser fornecida no mesmo objeto e esse objeto deve ser o elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9c5f-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9c5f-121">Remarks</span></span>

<span data-ttu-id="b9c5f-122">`x:Subclass` o uso destina-se principalmente a linguagens que não dão suporte a declarações de classe parciais.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="b9c5f-123">A classe usada como `x:Subclass` não pode ser uma classe aninhada e `x:Subclass` deve se referir ao objeto raiz, conforme explicado na seção "dependências".</span><span class="sxs-lookup"><span data-stu-id="b9c5f-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="b9c5f-124">Caso contrário, o significado conceitual de `x:Subclass` é indefinido por uma implementação de serviços XAML .net.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="b9c5f-125">Isso ocorre porque o comportamento dos serviços XAML .NET não especifica o modelo de programação geral pelo qual a marcação XAML e o código de suporte estão conectados.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="b9c5f-126">Implementações de outros conceitos relacionados ao `x:Class` e `x:Subclass` são executadas por estruturas específicas que usam modelos de programação ou modelos de aplicativos para definir como conectar marcação XAML, marcação compilada e code-behind baseado em CLR.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="b9c5f-127">Cada estrutura pode ter suas próprias ações de compilação que habilitam parte do comportamento ou componentes específicos que devem ser incluídos no ambiente de compilação.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="b9c5f-128">Dentro de uma estrutura, as ações de compilação também podem variar com base na linguagem CLR específica que é usada para o code-behind.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="b9c5f-129">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="b9c5f-129">WPF Usage Notes</span></span>

<span data-ttu-id="b9c5f-130">`x:Subclass` pode estar em uma raiz de página ou na <xref:System.Windows.Application> raiz na definição do aplicativo, que já tem `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="b9c5f-131">Declarar `x:Subclass` em qualquer elemento que não seja uma página ou raiz do aplicativo, ou especificá-lo onde não `x:Class` exista, causa um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="b9c5f-132">Criar classes derivadas que funcionam corretamente para o `x:Subclass` cenário é razoavelmente complexo.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="b9c5f-133">Talvez seja necessário examinar os arquivos intermediários (os arquivos. g produzidos na pasta obj do projeto por compilação de marcação, com nomes que incorporam os nomes de arquivo. XAML).</span><span class="sxs-lookup"><span data-stu-id="b9c5f-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="b9c5f-134">Esses arquivos intermediários podem ajudá-lo a determinar a origem de determinadas construções de programação nas classes parciais Unidas no aplicativo compilado.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="b9c5f-135">Manipuladores de eventos na classe derivada devem ser `internal override` ( `Friend Overrides` no Microsoft Visual Basic) para substituir os stubs para os manipuladores conforme criados na classe intermediária durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="b9c5f-136">Caso contrário, as implementações de classe derivada ocultam (Shadow) a implementação da classe intermediária e os manipuladores de classe intermediários não são invocados.</span><span class="sxs-lookup"><span data-stu-id="b9c5f-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="b9c5f-137">Quando você define `x:Class` e `x:Subclass` , não é necessário fornecer nenhuma implementação para a classe que é referenciada pelo `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="b9c5f-138">Você só precisa dar a ele um nome por meio do `x:Class` atributo para que o compilador tenha alguma orientação para a classe que ele cria nos arquivos intermediários (o compilador não seleciona um nome padrão nesse caso).</span><span class="sxs-lookup"><span data-stu-id="b9c5f-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="b9c5f-139">Você pode dar `x:Class` uma implementação à classe; no entanto, esse não é o cenário típico para usar o `x:Class` e o `x:Subclass` .</span><span class="sxs-lookup"><span data-stu-id="b9c5f-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9c5f-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9c5f-140">See also</span></span>

- [<span data-ttu-id="b9c5f-141">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="b9c5f-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="b9c5f-142">XAML e classes personalizadas para WPF</span><span class="sxs-lookup"><span data-stu-id="b9c5f-142">XAML and Custom Classes for WPF</span></span>](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
