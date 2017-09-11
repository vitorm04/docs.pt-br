---
title: 'Como: referenciar objetos COM do Visual Basic | Documentos do Microsoft'
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
- COM interop, referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
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
ms.openlocfilehash: 5f7f1112161d9be995cc80378ad9dd95c522198d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="2c6b3-102">Como fazer referência a objetos COM a partir do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c6b3-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="2c6b3-103">Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], adicionar referências a objetos COM que têm bibliotecas de tipo exige a criação de um assembly de interoperabilidade para a biblioteca COM.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="2c6b3-104">Referências para os membros do objeto COM são roteadas para o assembly de interoperabilidade e, em seguida, encaminhadas para o objeto COM real.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="2c6b3-105">Respostas do objeto COM são roteadas para o assembly de interoperabilidade e encaminhadas para a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span>  
  
 <span data-ttu-id="2c6b3-106">Você pode fazer referência a um objeto COM sem usar um assembly de interoperabilidade, incorporando as informações do tipo do objeto COM em um assembly do .NET.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="2c6b3-107">Para inserir informações de tipo, definir o `Embed Interop Types` propriedade `True` para a referência ao objeto COM.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="2c6b3-108">Se você estiver compilando usando o compilador de linha de comando, use o `/link` opção referenciar a biblioteca COM.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="2c6b3-109">Para obter mais informações, consulte [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="2c6b3-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2c6b3-110">cria automaticamente os assemblies de interoperabilidade, quando você adiciona uma referência a uma biblioteca de tipos do ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="2c6b3-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="2c6b3-111">Ao trabalhar na linha de comando, você pode usar o utilitário Tlbimp para criar manualmente os assemblies de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="2c6b3-112">Para adicionar referências a objetos COM</span><span class="sxs-lookup"><span data-stu-id="2c6b3-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="2c6b3-113">Sobre o **projeto** menu, escolha **adicionar referência** e, em seguida, clique no **COM** guia na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="2c6b3-114">Selecione o componente que você deseja usar na lista de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="2c6b3-115">Para simplificar o acesso ao assembly de interoperabilidade, adicione um `Imports` à parte superior da classe ou módulo que você irá usar o objeto COM.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="2c6b3-116">Por exemplo, o exemplo de código a seguir importa o namespace `INKEDLib` para objetos referenciados a `Microsoft InkEdit Control 1.0` biblioteca.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     <span data-ttu-id="2c6b3-117">[!code-vb[40 VbVbalrInterop](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2c6b3-117">[!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span></span>  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="2c6b3-118">Para criar um assembly de interoperabilidade usando Tlbimp</span><span class="sxs-lookup"><span data-stu-id="2c6b3-118">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="2c6b3-119">Adicione o local do Tlbimp ao caminho de pesquisa, se já não é parte do caminho de pesquisa e você não estiver no diretório onde ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-119">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="2c6b3-120">Chama Tlbimp a partir de um prompt de comando, fornecendo as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="2c6b3-120">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="2c6b3-121">Nome e local da DLL que contém a biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="2c6b3-121">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="2c6b3-122">Nome e localização do namespace onde as informações devem ser colocadas</span><span class="sxs-lookup"><span data-stu-id="2c6b3-122">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="2c6b3-123">Nome e local do assembly de interoperabilidade de destino</span><span class="sxs-lookup"><span data-stu-id="2c6b3-123">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="2c6b3-124">O código a seguir mostra um exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c6b3-124">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="2c6b3-125">Você pode usar Tlbimp para criar assemblies de interoperabilidade para bibliotecas de tipos, mesmo para objetos COM não registrados.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-125">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="2c6b3-126">No entanto, objetos COM referenciados por assemblies de interoperabilidade devem ser registrados corretamente no computador onde eles devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-126">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="2c6b3-127">Você pode registrar um objeto COM usando o utilitário Regsvr32 incluído com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="2c6b3-127">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6b3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c6b3-128">See Also</span></span>  
 <span data-ttu-id="2c6b3-129">[Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="2c6b3-129">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="2c6b3-130"> [Tlbimp.exe (importador de biblioteca)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span><span class="sxs-lookup"><span data-stu-id="2c6b3-130"> [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span></span>  
<span data-ttu-id="2c6b3-131"> [Tlbexp.exe (exportador da biblioteca)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span><span class="sxs-lookup"><span data-stu-id="2c6b3-131"> [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span></span>  
<span data-ttu-id="2c6b3-132"> [Passo a passo: Implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2c6b3-132"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="2c6b3-133"> [Solucionando problemas de interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span><span class="sxs-lookup"><span data-stu-id="2c6b3-133"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span></span>  
<span data-ttu-id="2c6b3-134"> [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span><span class="sxs-lookup"><span data-stu-id="2c6b3-134"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span></span>
