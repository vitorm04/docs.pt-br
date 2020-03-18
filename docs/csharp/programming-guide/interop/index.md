---
title: Interoperabilidade – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712046"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="b0add-102">Interoperabilidade (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b0add-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="b0add-103">A interoperabilidade permite que você mantenha e aproveite os investimentos existentes em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b0add-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="b0add-104">O código que é executado sob o controle do CLR (Common Language Runtime) é chamado de *código gerenciado*, e o código que é executado fora do CLR é chamado de *código não gerenciado*.</span><span class="sxs-lookup"><span data-stu-id="b0add-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="b0add-105">COM, COM+, componentes do C++, componentes do ActiveX e a API do Microsoft Windows são exemplos de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b0add-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="b0add-106">O .NET Framework habilita a interoperabilidade com código não gerenciado por meio de serviços de invocação de plataforma, o <xref:System.Runtime.InteropServices> namespace, a interoperabilidade com C++ e a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="b0add-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0add-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b0add-107">In This Section</span></span>  
 [<span data-ttu-id="b0add-108">Visão geral sobre interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b0add-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="b0add-109">Descreve métodos para fins de interoperabilidade entre código gerenciado em C# e código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b0add-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="b0add-110">Como acessar objetos de interoperabilidade do Office usando recursos do C#</span><span class="sxs-lookup"><span data-stu-id="b0add-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="b0add-111">Descreve os recursos que são introduzidos no Visual C# para facilitar a programação do Office.</span><span class="sxs-lookup"><span data-stu-id="b0add-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="b0add-112">Como usar propriedades indexadas na programação para interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="b0add-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="b0add-113">Descreve como usar propriedades indexadas para acesso propriedades COM que têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b0add-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="b0add-114">Como usar invocação de plataforma para executar um arquivo WAV</span><span class="sxs-lookup"><span data-stu-id="b0add-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="b0add-115">Descreve como usar os serviços de invocação de plataforma para reproduzir um arquivo de som .wav no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="b0add-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="b0add-116">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="b0add-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="b0add-117">Mostra como criar uma planilha do Excel e um documento do Word com um link para a planilha.</span><span class="sxs-lookup"><span data-stu-id="b0add-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="b0add-118">Exemplo de classe COM</span><span class="sxs-lookup"><span data-stu-id="b0add-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="b0add-119">Demonstra como expor uma classe C# como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="b0add-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b0add-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b0add-120">C# Language Specification</span></span>  

<span data-ttu-id="b0add-121">Para obter mais informações, veja [Noções básicas](~/_csharplang/spec/unsafe-code.md) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b0add-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="b0add-122">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="b0add-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b0add-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="b0add-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b0add-124">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="b0add-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b0add-125">Interoperação com Código Não Gerenciado</span><span class="sxs-lookup"><span data-stu-id="b0add-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="b0add-126">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="b0add-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
