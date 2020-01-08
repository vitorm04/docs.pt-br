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
ms.openlocfilehash: 64fac0245dcf5976786b51e0d96b795b8b1e5d68
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635191"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="cf159-102">Interoperabilidade (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="cf159-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="cf159-103">A interoperabilidade permite que você mantenha e aproveite os investimentos existentes em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="cf159-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="cf159-104">O código que é executado sob o controle do CLR (Common Language Runtime) é chamado de *código gerenciado*, e o código que é executado fora do CLR é chamado de *código não gerenciado*.</span><span class="sxs-lookup"><span data-stu-id="cf159-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="cf159-105">COM, COM+, componentes do C++, componentes do ActiveX e a API do Microsoft Windows são exemplos de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="cf159-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="cf159-106">O .NET Framework habilita a interoperabilidade com código não gerenciado por meio de serviços de invocação de plataforma, o <xref:System.Runtime.InteropServices> namespace, a interoperabilidade com C++ e a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="cf159-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf159-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cf159-107">In This Section</span></span>  
 [<span data-ttu-id="cf159-108">Visão geral sobre interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="cf159-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="cf159-109">Descreve métodos para fins de interoperabilidade entre código gerenciado em C# e código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="cf159-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="cf159-110">Como acessar objetos de interoperabilidade do C# Office usando recursos</span><span class="sxs-lookup"><span data-stu-id="cf159-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="cf159-111">Descreve os recursos que são introduzidos no Visual C# para facilitar a programação do Office.</span><span class="sxs-lookup"><span data-stu-id="cf159-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="cf159-112">Como usar propriedades indexadas na programação de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="cf159-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="cf159-113">Descreve como usar propriedades indexadas para acesso propriedades COM que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cf159-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="cf159-114">Como usar a invocação de plataforma para reproduzir um arquivo WAV</span><span class="sxs-lookup"><span data-stu-id="cf159-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="cf159-115">Descreve como usar os serviços de invocação de plataforma para reproduzir um arquivo de som .wav no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="cf159-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="cf159-116">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="cf159-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="cf159-117">Mostra como criar uma planilha do Excel e um documento do Word com um link para a planilha.</span><span class="sxs-lookup"><span data-stu-id="cf159-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="cf159-118">Exemplo de classe COM</span><span class="sxs-lookup"><span data-stu-id="cf159-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="cf159-119">Demonstra como expor uma classe C# como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="cf159-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cf159-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cf159-120">C# Language Specification</span></span>  

<span data-ttu-id="cf159-121">Para obter mais informações, veja [Noções básicas](~/_csharplang/spec/unsafe-code.md) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="cf159-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="cf159-122">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="cf159-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cf159-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf159-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cf159-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cf159-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cf159-125">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="cf159-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="cf159-126">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="cf159-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
