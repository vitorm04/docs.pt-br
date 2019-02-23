---
title: Referências e a instrução Imports (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: d9a227f60edf142832ab41e3ea99f33c53a42229
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748304"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="921f8-102">Referências e a instrução Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="921f8-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="921f8-103">Você pode disponibilizar objetos externos ao seu projeto, escolhendo a **adicionar referência** comando as **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="921f8-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="921f8-104">As referências no Visual Basic podem apontar para assemblies, que são como as bibliotecas de tipos, mas contêm mais informações.</span><span class="sxs-lookup"><span data-stu-id="921f8-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="921f8-105">A instrução Imports</span><span class="sxs-lookup"><span data-stu-id="921f8-105">The Imports Statement</span></span>  
 <span data-ttu-id="921f8-106">Assemblies incluem um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="921f8-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="921f8-107">Quando você adiciona uma referência a um assembly, você também pode adicionar um `Imports` instrução para um módulo que controla a visibilidade dos namespaces daquele assembly dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="921f8-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="921f8-108">O `Imports` instrução fornece um contexto de escopo que permite que você use apenas a parte do namespace necessária para fornecer uma referência única.</span><span class="sxs-lookup"><span data-stu-id="921f8-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="921f8-109">O `Imports` instrução tem a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="921f8-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="921f8-110">`Aliasname` se refere a um nome curto que você pode usar dentro do código para se referir a um namespace importado.</span><span class="sxs-lookup"><span data-stu-id="921f8-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="921f8-111">`Namespace` é um namespace disponível por meio de uma referência de projeto, por meio de uma definição de dentro do projeto, ou por meio de um anterior `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="921f8-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="921f8-112">Um módulo pode conter qualquer número de `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="921f8-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="921f8-113">Elas devem aparecer após qualquer `Option` instruções, se estiver presente, mas antes de qualquer outro código.</span><span class="sxs-lookup"><span data-stu-id="921f8-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="921f8-114">Não confunda referências de projeto com o `Imports` instrução ou o `Declare` instrução.</span><span class="sxs-lookup"><span data-stu-id="921f8-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="921f8-115">Referências de projeto tornam objetos externos, como objetos em assemblies, disponíveis para projetos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="921f8-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="921f8-116">O `Imports` instrução é usada para simplificar o acesso às referências do projeto, mas não fornece acesso a esses objetos.</span><span class="sxs-lookup"><span data-stu-id="921f8-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="921f8-117">O `Declare` instrução é usada para declarar uma referência a um procedimento externo em uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="921f8-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="921f8-118">Usando Aliases com a instrução Imports</span><span class="sxs-lookup"><span data-stu-id="921f8-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="921f8-119">O `Imports` instrução torna mais fácil para os métodos de acesso de classes, eliminando a necessidade de digitar explicitamente os nomes totalmente qualificados de referências.</span><span class="sxs-lookup"><span data-stu-id="921f8-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="921f8-120">Os aliases permitem que você atribua um nome amigável para apenas uma parte de um namespace.</span><span class="sxs-lookup"><span data-stu-id="921f8-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="921f8-121">Por exemplo, o retorno de carro/linha sequência que faz com que uma única parte do texto a ser exibido em várias linhas do feed é parte do <xref:Microsoft.VisualBasic.ControlChars> módulo no <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="921f8-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="921f8-122">Para usar essa constante em um programa sem um alias, você precisa digitar o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="921f8-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="921f8-123">`Imports` instruções sempre devem ser as primeiras linhas imediatamente após qualquer `Option` instruções em um módulo.</span><span class="sxs-lookup"><span data-stu-id="921f8-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="921f8-124">O fragmento de código a seguir mostra como importar e atribuir um alias para o <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> módulo:</span><span class="sxs-lookup"><span data-stu-id="921f8-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="921f8-125">Referências futuras para esse namespace podem ser consideravelmente menores:</span><span class="sxs-lookup"><span data-stu-id="921f8-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="921f8-126">Se um `Imports` instrução não incluir um nome de alias, elementos definidos no namespace importado podem ser usados no módulo sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="921f8-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="921f8-127">Se o nome do alias for especificado, ele deve ser usado como um qualificador para nomes contidos dentro desse namespace.</span><span class="sxs-lookup"><span data-stu-id="921f8-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921f8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="921f8-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="921f8-129">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="921f8-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="921f8-130">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="921f8-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- <span data-ttu-id="921f8-131">[Como: criar e usar assemblies usando a linha de comando](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="921f8-131">[How to: Create and Use Assemblies Using the Command Line](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)</span></span>
- [<span data-ttu-id="921f8-132">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="921f8-132">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
