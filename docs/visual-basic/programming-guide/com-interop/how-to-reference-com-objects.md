---
title: Como fazer referência a objetos COM a partir do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: ea0e1d9b0ae9f151d901c425512508ba7bc05343
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524360"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="68762-102">Como fazer referência a objetos COM a partir do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68762-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="68762-103">No Visual Basic, a adição de referências a objetos COM que têm bibliotecas de tipos requer a criação de um assembly de interoperabilidade para a biblioteca COM.</span><span class="sxs-lookup"><span data-stu-id="68762-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="68762-104">As referências aos membros do objeto COM são roteadas para o assembly de interoperabilidade e, em seguida, encaminhadas para o objeto COM real.</span><span class="sxs-lookup"><span data-stu-id="68762-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="68762-105">As respostas do objeto COM são roteadas para o assembly de interoperabilidade e encaminhadas para seu aplicativo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68762-105">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="68762-106">Você pode referenciar um objeto COM sem usar um assembly de interoperabilidade inserindo as informações de tipo para o objeto COM em um assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="68762-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="68762-107">Para inserir informações de tipo, defina a propriedade `Embed Interop Types` como `True` para a referência ao objeto COM.</span><span class="sxs-lookup"><span data-stu-id="68762-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="68762-108">Se você estiver compilando usando o compilador de linha de comando, use a opção `/link` para fazer referência à biblioteca COM.</span><span class="sxs-lookup"><span data-stu-id="68762-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="68762-109">Para obter mais informações, consulte [-link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="68762-109">For more information, see [-link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="68762-110">Visual Basic cria automaticamente assemblies de interoperabilidade quando você adiciona uma referência a uma biblioteca de tipos do ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="68762-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="68762-111">Ao trabalhar na linha de comando, você pode usar o utilitário TLBIMP para criar manualmente assemblies de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="68762-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="68762-112">Para adicionar referências a objetos COM</span><span class="sxs-lookup"><span data-stu-id="68762-112">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="68762-113">No menu **projeto** , escolha **Adicionar referência** e, em seguida, clique na guia **com** na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="68762-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="68762-114">Selecione o componente que você deseja usar na lista de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="68762-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="68762-115">Para simplificar o acesso ao assembly de interoperabilidade, adicione uma instrução `Imports` à parte superior da classe ou do módulo no qual você usará o objeto COM.</span><span class="sxs-lookup"><span data-stu-id="68762-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="68762-116">Por exemplo, o exemplo de código a seguir importa o namespace `INKEDLib` para objetos referenciados na biblioteca `Microsoft InkEdit Control 1.0`.</span><span class="sxs-lookup"><span data-stu-id="68762-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="68762-117">Para criar um assembly de interoperabilidade usando Tlbimp</span><span class="sxs-lookup"><span data-stu-id="68762-117">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="68762-118">Adicione o local do Tlbimp ao caminho de pesquisa, se ele ainda não faz parte do caminho de pesquisa e você não está no diretório onde ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="68762-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="68762-119">Chame Tlbimp em um prompt de comando, fornecendo as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="68762-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="68762-120">Nome e local da DLL que contém a biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="68762-120">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="68762-121">Nome e local do namespace onde as informações devem ser colocadas</span><span class="sxs-lookup"><span data-stu-id="68762-121">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="68762-122">Nome e local do assembly de interoperabilidade de destino</span><span class="sxs-lookup"><span data-stu-id="68762-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="68762-123">O código a seguir mostra um exemplo:</span><span class="sxs-lookup"><span data-stu-id="68762-123">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="68762-124">Você pode usar Tlbimp para criar assemblies de interoperabilidade para bibliotecas de tipos, mesmo para objetos COM não registrados.</span><span class="sxs-lookup"><span data-stu-id="68762-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="68762-125">No entanto, os objetos COM referenciados por assemblies de interoperabilidade devem ser registrados corretamente no computador onde eles devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="68762-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="68762-126">Você pode registrar um objeto COM usando o utilitário regsvr32 incluído no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="68762-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68762-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68762-127">See also</span></span>

- [<span data-ttu-id="68762-128">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="68762-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="68762-129">Tlbimp.exe (Importador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="68762-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="68762-130">Tlbexp.exe (Exportador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="68762-130">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="68762-131">Instruções passo a passo: implementando a herança com objetos COM</span><span class="sxs-lookup"><span data-stu-id="68762-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="68762-132">Solução de problemas de Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="68762-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [<span data-ttu-id="68762-133">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="68762-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
