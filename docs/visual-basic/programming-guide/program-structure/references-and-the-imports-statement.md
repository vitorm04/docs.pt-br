---
title: "Referências e a instrução Imports (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references, assembly
- namespaces, assemblies
- referencing assemblies
- Imports statement, referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4c6ce65005f84317c96a1124d609c46734d3cc66
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="c70bb-102">Referências e a instrução Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c70bb-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="c70bb-103">Você pode tornar externos objetos disponíveis para seu projeto, escolhendo o **adicionar referência** comando o **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="c70bb-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="c70bb-104">Referências em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pode apontar para assemblies, que são como bibliotecas mas contêm mais informações.</span><span class="sxs-lookup"><span data-stu-id="c70bb-104">References in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="c70bb-105">A instrução Imports</span><span class="sxs-lookup"><span data-stu-id="c70bb-105">The Imports Statement</span></span>  
 <span data-ttu-id="c70bb-106">Módulos (assemblies) incluem um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="c70bb-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="c70bb-107">Quando você adiciona uma referência a um assembly, você também pode adicionar uma `Imports` instrução em um módulo que controla a visibilidade dos namespaces daquele assembly dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="c70bb-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="c70bb-108">O `Imports` instrução fornece um contexto de escopo que permite que você use apenas a parte do namespace necessária para fornecer uma referência única.</span><span class="sxs-lookup"><span data-stu-id="c70bb-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="c70bb-109">O `Imports` instrução tem a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="c70bb-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="c70bb-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="c70bb-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="c70bb-111">`Aliasname`refere-se a um nome curto que você pode usar dentro de código para se referir a um namespace importado.</span><span class="sxs-lookup"><span data-stu-id="c70bb-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="c70bb-112">`Namespace`é um namespace disponível através de uma referência de projeto, por meio de uma definição do projeto ou anterior `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="c70bb-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="c70bb-113">Um módulo pode conter qualquer número de `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="c70bb-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="c70bb-114">Elas devem aparecer após qualquer `Option` instruções, se presente, mas antes de qualquer outro código.</span><span class="sxs-lookup"><span data-stu-id="c70bb-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c70bb-115">Não confunda referências de projeto com o `Imports` instrução ou o `Declare` instrução.</span><span class="sxs-lookup"><span data-stu-id="c70bb-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="c70bb-116">Referências de projeto tornam objetos externos, como objetos em assemblies, disponível para [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projetos.</span><span class="sxs-lookup"><span data-stu-id="c70bb-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projects.</span></span> <span data-ttu-id="c70bb-117">O `Imports` instrução é usada para simplificar o acesso às referências do projeto, mas não fornece acesso a esses objetos.</span><span class="sxs-lookup"><span data-stu-id="c70bb-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="c70bb-118">O `Declare` instrução é usada para declarar uma referência a um procedimento externo em uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="c70bb-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="c70bb-119">Usando Aliases com a instrução Imports</span><span class="sxs-lookup"><span data-stu-id="c70bb-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="c70bb-120">O `Imports` instrução torna mais fácil acessar os métodos de classes, eliminando a necessidade de digitar explicitamente os nomes totalmente qualificados de referências.</span><span class="sxs-lookup"><span data-stu-id="c70bb-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="c70bb-121">Os aliases permitem que você atribua um nome amigável a apenas uma parte de um namespace.</span><span class="sxs-lookup"><span data-stu-id="c70bb-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="c70bb-122">Por exemplo, o retorno de carro/linha alimentação sequência que faz com que uma única parte do texto a ser exibido em várias linhas é parte do <xref:Microsoft.VisualBasic.ControlChars>módulo o <xref:Microsoft.VisualBasic?displayProperty=fullName>namespace.</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="c70bb-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="c70bb-123">Para usar essa constante em um programa sem um alias, você precisa digitar o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c70bb-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 <span data-ttu-id="c70bb-124">[!code-vb[VbVbalrApplication n º&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c70bb-124">[!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="c70bb-125">`Imports`instruções devem sempre ser as primeiras linhas imediatamente após quaisquer `Option` instruções em um módulo.</span><span class="sxs-lookup"><span data-stu-id="c70bb-125">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="c70bb-126">O fragmento de código a seguir mostra como importar e atribuir um alias para o <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>módulo:</xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c70bb-126">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName> module:</span></span>  
  
 <span data-ttu-id="c70bb-127">[!code-vb[VbVbalrApplication n º&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c70bb-127">[!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="c70bb-128">Referências futuras a esse namespace podem ser consideravelmente menores:</span><span class="sxs-lookup"><span data-stu-id="c70bb-128">Future references to this namespace can be considerably shorter:</span></span>  
  
 <span data-ttu-id="c70bb-129">[!code-vb[VbVbalrApplication n º&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c70bb-129">[!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="c70bb-130">Se um `Imports` instrução não incluir um nome de alias, elementos definidos no namespace importado podem ser usados no módulo sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="c70bb-130">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="c70bb-131">Se o nome do alias for especificado, ele deve ser usado como um qualificador para nomes contidos naquele namespace.</span><span class="sxs-lookup"><span data-stu-id="c70bb-131">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70bb-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c70bb-132">See Also</span></span>  
 <span data-ttu-id="c70bb-133"><xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="c70bb-133"><xref:Microsoft.VisualBasic.ControlChars></span></span>   
 <span data-ttu-id="c70bb-134"><xref:Microsoft.VisualBasic></xref:Microsoft.VisualBasic></span><span class="sxs-lookup"><span data-stu-id="c70bb-134"><xref:Microsoft.VisualBasic></span></span>   
<span data-ttu-id="c70bb-135"> [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="c70bb-135"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="c70bb-136"> [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="c70bb-136"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="c70bb-137"> [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="c70bb-137"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="c70bb-138"> [Como: criar e usar Assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span><span class="sxs-lookup"><span data-stu-id="c70bb-138"> [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span></span>  
<span data-ttu-id="c70bb-139"> [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span><span class="sxs-lookup"><span data-stu-id="c70bb-139"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span></span>
