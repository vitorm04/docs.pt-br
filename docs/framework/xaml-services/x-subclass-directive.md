---
title: Diretiva x:Subclass
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: 20
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 566b772db0e8f96c3272481d47b3e220f727d95b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="xsubclass-directive"></a><span data-ttu-id="f9bac-102">Diretiva x:Subclass</span><span class="sxs-lookup"><span data-stu-id="f9bac-102">x:Subclass Directive</span></span>
<span data-ttu-id="f9bac-103">Modifica o comportamento de compilação de marcação XAML quando `x:Class` também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="f9bac-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="f9bac-104">Em vez de criar uma classe parcial que é baseada no `x:Class`, fornecido `x:Class` é criado como uma classe intermediária, e, em seguida, espera-se que a classe derivada fornecida seja baseada em `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f9bac-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="f9bac-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f9bac-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="f9bac-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="f9bac-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f9bac-107">Optional.</span></span> <span data-ttu-id="f9bac-108">Especifica um namespace CLR que contém `classname`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="f9bac-109">Se `namespace` for especificado, um ponto (.) separa `namespace` e `classname`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="f9bac-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f9bac-110">Required.</span></span> <span data-ttu-id="f9bac-111">Especifica o nome CLR da classe parcial que conecta o XAML carregado e o code-behind para esse XAML.</span><span class="sxs-lookup"><span data-stu-id="f9bac-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="f9bac-112">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="f9bac-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="f9bac-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f9bac-113">Optional.</span></span> <span data-ttu-id="f9bac-114">Pode ser diferente da `namespace` se cada namespace possa resolver o outro.</span><span class="sxs-lookup"><span data-stu-id="f9bac-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="f9bac-115">Especifica um namespace CLR que contém `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="f9bac-116">Se `subclassName` for especificado, um ponto (.) separa `subclassNamespace` e `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="f9bac-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f9bac-117">Required.</span></span> <span data-ttu-id="f9bac-118">Especifica o nome da subclasse do CLR.</span><span class="sxs-lookup"><span data-stu-id="f9bac-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="f9bac-119">Dependências</span><span class="sxs-lookup"><span data-stu-id="f9bac-119">Dependencies</span></span>  
 <span data-ttu-id="f9bac-120">[Diretiva X:Class](../../../docs/framework/xaml-services/x-class-directive.md) também deve ser fornecido no mesmo objeto, e esse objeto deve ser o elemento raiz de produção XAML.</span><span class="sxs-lookup"><span data-stu-id="f9bac-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9bac-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9bac-121">Remarks</span></span>  
 <span data-ttu-id="f9bac-122">`x:Subclass` uso destina-se principalmente a idiomas que não oferecem suporte a declarações de classe parcial.</span><span class="sxs-lookup"><span data-stu-id="f9bac-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="f9bac-123">A classe usada como o `x:Subclass` não pode ser uma classe aninhada, e `x:Subclass` devem se referir ao objeto raiz conforme explicado na seção "Dependências".</span><span class="sxs-lookup"><span data-stu-id="f9bac-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="f9bac-124">Caso contrário, o significado conceitual de `x:Subclass` não está definida por uma implementação de serviços XAML do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9bac-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="f9bac-125">Isso ocorre porque o comportamento de serviços XAML do .NET Framework não especifica o modelo de programação geral pelo qual XAML marcação e código de backup estão conectados.</span><span class="sxs-lookup"><span data-stu-id="f9bac-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="f9bac-126">Implementações de ainda mais os conceitos relacionados a `x:Class` e `x:Subclass` são executadas por estruturas específicas que usam modelos de programação ou modelos de aplicativo para definir como conectar-se a marcação XAML, marcação compilada e com base em CLR code-behind.</span><span class="sxs-lookup"><span data-stu-id="f9bac-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="f9bac-127">Cada estrutura pode ter sua própria ações de compilação que permitem alguns comportamento ou componentes específicos que devem ser incluídos no ambiente de compilação.</span><span class="sxs-lookup"><span data-stu-id="f9bac-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="f9bac-128">Em uma estrutura, ações de compilação também podem variar com base no idioma específico do CLR que é usado para o code-behind.</span><span class="sxs-lookup"><span data-stu-id="f9bac-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="f9bac-129">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="f9bac-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="f9bac-130">`x:Subclass` pode ser em uma raiz de página ou no <xref:System.Windows.Application> raiz na definição de aplicativo, que já tenha `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="f9bac-131">Declarando `x:Subclass` em qualquer elemento que não seja uma raiz de aplicativo ou página ou especificá-lo onde nenhum `x:Class` existe, causa um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f9bac-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="f9bac-132">Criar classes derivadas que funcionam corretamente para o `x:Subclass` cenário é relativamente complexo.</span><span class="sxs-lookup"><span data-stu-id="f9bac-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="f9bac-133">Talvez seja necessário examinar os arquivos intermediários (os arquivos. g produzidos na pasta obj do seu projeto pela compilação de marcação, com nomes que incorporam os nomes de arquivo. XAML).</span><span class="sxs-lookup"><span data-stu-id="f9bac-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="f9bac-134">Esses arquivos intermediários podem ajudá-lo a determinar a origem de determinadas construções de programação nas classes parciais associadas no aplicativo compilado.</span><span class="sxs-lookup"><span data-stu-id="f9bac-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="f9bac-135">Manipuladores de eventos na classe derivada devem ser `internal override` (`Friend Overrides` no Microsoft Visual Basic) para substituir os stubs para os manipuladores que foi criado na classe intermediária durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="f9bac-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="f9bac-136">Caso contrário, as implementações de classe derivada ocultar (sombra) a implementação da classe intermediária e manipuladores de classe intermediários não são invocados.</span><span class="sxs-lookup"><span data-stu-id="f9bac-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="f9bac-137">Quando você define tanto `x:Class` e `x:Subclass`, você não precisa fornecer qualquer implementação para a classe que é referenciada por `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="f9bac-138">Você só precisa dar um nome por meio de `x:Class` atributo para que o compilador tenha alguma orientação para a classe que ele cria nos arquivos intermediários (o compilador não selecione um nome padrão neste caso).</span><span class="sxs-lookup"><span data-stu-id="f9bac-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="f9bac-139">Você pode dar a `x:Class` uma implementação da classe; no entanto, isso não é o cenário típico para usar tanto `x:Class` e `x:Subclass`.</span><span class="sxs-lookup"><span data-stu-id="f9bac-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bac-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9bac-140">See Also</span></span>  
 [<span data-ttu-id="f9bac-141">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="f9bac-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="f9bac-142">XAML e classes personalizadas para WPF</span><span class="sxs-lookup"><span data-stu-id="f9bac-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
