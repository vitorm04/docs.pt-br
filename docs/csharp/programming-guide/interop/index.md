---
title: Interoperabilidade – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: f3cbfe564fb5820c9e0fa77b75f76be36dd718a4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235001"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="e07d7-102">Interoperabilidade (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e07d7-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="e07d7-103">A interoperabilidade permite que você mantenha e aproveite os investimentos existentes em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e07d7-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="e07d7-104">O código que é executado sob o controle do CLR (Common Language Runtime) é chamado de *código gerenciado*, e o código que é executado fora do CLR é chamado de *código não gerenciado*.</span><span class="sxs-lookup"><span data-stu-id="e07d7-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="e07d7-105">COM, COM+, componentes do C++, componentes do ActiveX e a API do Microsoft Win32 são exemplos de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e07d7-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="e07d7-106">O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] habilita a interoperabilidade com código não gerenciado por meio de serviços de invocação de plataforma, o namespace <xref:System.Runtime.InteropServices>, a interoperabilidade com C++ e a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="e07d7-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e07d7-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e07d7-107">In This Section</span></span>  
 [<span data-ttu-id="e07d7-108">Visão geral sobre interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="e07d7-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="e07d7-109">Descreve métodos para fins de interoperabilidade entre código gerenciado em C# e código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e07d7-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="e07d7-110">Como: acessar objetos de interoperabilidade do Office usando recursos do Visual C#</span><span class="sxs-lookup"><span data-stu-id="e07d7-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="e07d7-111">Descreve os recursos que são introduzidos no Visual C# para facilitar a programação do Office.</span><span class="sxs-lookup"><span data-stu-id="e07d7-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="e07d7-112">Como: usar propriedades indexadas na programação para interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="e07d7-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="e07d7-113">Descreve como usar propriedades indexadas para acesso propriedades COM que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e07d7-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="e07d7-114">Como: usar invocação de plataforma para executar um arquivo wave</span><span class="sxs-lookup"><span data-stu-id="e07d7-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="e07d7-115">Descreve como usar os serviços de invocação de plataforma para reproduzir um arquivo de som .wav no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="e07d7-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="e07d7-116">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="e07d7-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="e07d7-117">Mostra como criar uma planilha do Excel e um documento do Word com um link para a planilha.</span><span class="sxs-lookup"><span data-stu-id="e07d7-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="e07d7-118">Exemplo de classe COM</span><span class="sxs-lookup"><span data-stu-id="e07d7-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="e07d7-119">Demonstra como expor uma classe C# como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="e07d7-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e07d7-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e07d7-120">C# Language Specification</span></span>  

<span data-ttu-id="e07d7-121">Para obter mais informações, veja [Noções básicas](~/_csharplang/spec/unsafe-code.md) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e07d7-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="e07d7-122">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="e07d7-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e07d7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e07d7-123">See Also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="e07d7-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e07d7-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e07d7-125">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="e07d7-125">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
- [<span data-ttu-id="e07d7-126">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="e07d7-126">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
