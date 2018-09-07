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
ms.openlocfilehash: 293bf76b1520f50e67837942eab2f27a49e330e3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081568"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="89626-102">Como fazer referência a objetos COM a partir do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89626-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="89626-103">No Visual Basic, a adição de referências a objetos COM que têm bibliotecas de tipo requer a criação de um assembly de interoperabilidade para a biblioteca COM.</span><span class="sxs-lookup"><span data-stu-id="89626-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="89626-104">As referências aos membros do objeto COM são roteadas para o assembly de interoperabilidade e, em seguida, encaminhadas para o objeto COM real.</span><span class="sxs-lookup"><span data-stu-id="89626-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="89626-105">As respostas do objeto COM são roteadas para o assembly de interoperabilidade e encaminhadas para seu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89626-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="89626-106">Você pode fazer referência a um objeto COM sem o uso de um assembly de interoperabilidade, incorporando as informações de tipo para o objeto COM em um assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="89626-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="89626-107">Para inserir informações de tipo, defina as `Embed Interop Types` propriedade para `True` para a referência ao objeto COM.</span><span class="sxs-lookup"><span data-stu-id="89626-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="89626-108">Se você estiver compilando usando o compilador de linha de comando, use o `/link` opção para fazer referência a biblioteca COM.</span><span class="sxs-lookup"><span data-stu-id="89626-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="89626-109">Para obter mais informações, consulte [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="89626-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="89626-110">Visual Basic cria automaticamente os assemblies de interoperabilidade quando você adiciona uma referência a uma biblioteca de tipos de ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="89626-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="89626-111">Ao trabalhar na linha de comando, você pode usar o utilitário Tlbimp para criar manualmente os assemblies de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="89626-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="89626-112">Para adicionar referências a objetos COM</span><span class="sxs-lookup"><span data-stu-id="89626-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="89626-113">Sobre o **projeto** menu, escolha **adicionar referência** e, em seguida, clique no **COM** guia na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="89626-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="89626-114">Selecione o componente que você deseja usar na lista de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="89626-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="89626-115">Para simplificar o acesso ao assembly de interoperabilidade, adicione um `Imports` instrução na parte superior da classe ou módulo que você usará o objeto COM.</span><span class="sxs-lookup"><span data-stu-id="89626-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="89626-116">Por exemplo, o exemplo de código a seguir importa o namespace `INKEDLib` para objetos referenciados no `Microsoft InkEdit Control 1.0` biblioteca.</span><span class="sxs-lookup"><span data-stu-id="89626-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="89626-117">Para criar um assembly de interoperabilidade usando Tlbimp</span><span class="sxs-lookup"><span data-stu-id="89626-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="89626-118">Adicione o local do Tlbimp ao caminho de pesquisa, se ele não ainda faz parte do caminho de pesquisa e você não estiver atualmente no diretório onde ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="89626-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="89626-119">Tlbimp chamada em um prompt de comando, fornecendo as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="89626-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="89626-120">Nome e o local da DLL que contém a biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="89626-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="89626-121">Nome e o local do namespace onde as informações devem ser colocadas</span><span class="sxs-lookup"><span data-stu-id="89626-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="89626-122">Nome e local do assembly de interoperabilidade de destino</span><span class="sxs-lookup"><span data-stu-id="89626-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="89626-123">O código a seguir mostra um exemplo:</span><span class="sxs-lookup"><span data-stu-id="89626-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="89626-124">Você pode usar Tlbimp para criar assemblies de interoperabilidade para bibliotecas de tipos, mesmo para objetos COM não registrados.</span><span class="sxs-lookup"><span data-stu-id="89626-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="89626-125">No entanto, os objetos COM referenciados por assemblies de interoperabilidade devem ser registrados corretamente no computador em que eles devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="89626-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="89626-126">Você pode registrar um objeto COM por meio do utilitário Regsvr32 incluído com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="89626-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89626-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89626-127">See also</span></span>

- [<span data-ttu-id="89626-128">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="89626-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
- [<span data-ttu-id="89626-129">Tlbimp.exe (Importador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="89626-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
- [<span data-ttu-id="89626-130">Tlbexp.exe (Exportador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="89626-130">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)  
- [<span data-ttu-id="89626-131">Instruções passo a passo: implementando a herança com objetos COM</span><span class="sxs-lookup"><span data-stu-id="89626-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
- [<span data-ttu-id="89626-132">Solução de problemas de Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="89626-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
- [<span data-ttu-id="89626-133">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="89626-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
