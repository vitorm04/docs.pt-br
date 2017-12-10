---
title: "Interoperabilidade (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2965543066b0846a6a4f8a3199590049947122f2
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="2b559-102">Interoperabilidade (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2b559-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="2b559-103">A interoperabilidade permite que você mantenha e aproveite os investimentos existentes em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2b559-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="2b559-104">O código que é executado sob o controle do CLR (Common Language Runtime) é chamado de *código gerenciado*, e o código que é executado fora do CLR é chamado de *código não gerenciado*.</span><span class="sxs-lookup"><span data-stu-id="2b559-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="2b559-105">COM, COM+, componentes do C++, componentes do ActiveX e a API do Microsoft Win32 são exemplos de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2b559-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="2b559-106">O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] habilita a interoperabilidade com código não gerenciado por meio de serviços de invocação de plataforma, o namespace <xref:System.Runtime.InteropServices>, a interoperabilidade com C++ e a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="2b559-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b559-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2b559-107">In This Section</span></span>  
 [<span data-ttu-id="2b559-108">Visão geral sobre interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="2b559-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="2b559-109">Descreve métodos para fins de interoperabilidade entre código gerenciado em C# e código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2b559-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="2b559-110">Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#</span><span class="sxs-lookup"><span data-stu-id="2b559-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="2b559-111">Descreve os recursos que são introduzidos no Visual C# para facilitar a programação do Office.</span><span class="sxs-lookup"><span data-stu-id="2b559-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="2b559-112">Como usar propriedades indexadas na programação para interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="2b559-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="2b559-113">Descreve como usar propriedades indexadas para acesso propriedades COM que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2b559-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="2b559-114">Como usar invocação de plataforma para executar um arquivo wave</span><span class="sxs-lookup"><span data-stu-id="2b559-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="2b559-115">Descreve como usar os serviços de invocação de plataforma para reproduzir um arquivo de som .wav no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="2b559-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="2b559-116">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="2b559-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="2b559-117">Mostra como criar uma planilha do Excel e um documento do Word com um link para a planilha.</span><span class="sxs-lookup"><span data-stu-id="2b559-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="2b559-118">Exemplo de classe COM</span><span class="sxs-lookup"><span data-stu-id="2b559-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="2b559-119">Demonstra como expor uma classe C# como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="2b559-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2b559-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2b559-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b559-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b559-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2b559-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2b559-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2b559-123">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="2b559-123">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="2b559-124">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="2b559-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
