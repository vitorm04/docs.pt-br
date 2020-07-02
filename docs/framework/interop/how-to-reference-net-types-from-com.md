---
title: 'Como: Referenciar tipos .NET por meio do COM'
description: Referencie tipos .NET de COM. Os clientes do VB podem exibir um objeto .NET no Pesquisador de objetos, mas os clientes do C++ devem fazer referência a um arquivo TLB com a \# diretiva de importação.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: f8d052c7b9bac9c4bab61ab1950e9e89a7c73912
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618955"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="e00d9-104">Como: Referenciar tipos .NET por meio do COM</span><span class="sxs-lookup"><span data-stu-id="e00d9-104">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="e00d9-105">Do ponto de vista do código de cliente e servidor, as diferenças entre o .NET Framework e o COM são bastante invisíveis.</span><span class="sxs-lookup"><span data-stu-id="e00d9-105">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="e00d9-106">Os clientes do Microsoft Visual Basic podem exibir um objeto .NET no Pesquisador de Objetos, que expõe os métodos de objeto e a sintaxe, propriedades e campos exatamente como se fosse qualquer outro objeto COM.</span><span class="sxs-lookup"><span data-stu-id="e00d9-106">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="e00d9-107">O processo de importação de uma biblioteca de tipos é um pouco mais complicado para clientes do C++, embora você use as mesmas ferramentas para exportar metadados para uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="e00d9-107">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="e00d9-108">Para referenciar membros do objeto .NET de um cliente C++ não gerenciado, referencie o arquivo TLB (produzido com Tlbexp.exe) com a diretiva **#import**.</span><span class="sxs-lookup"><span data-stu-id="e00d9-108">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="e00d9-109">Ao referenciar uma biblioteca de tipos C++, você deve especificar a opção **raw_interfaces_only** ou importar as definições na biblioteca de classes base, Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="e00d9-109">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="e00d9-110">Para importar uma biblioteca</span><span class="sxs-lookup"><span data-stu-id="e00d9-110">To import a library</span></span>  
  
- <span data-ttu-id="e00d9-111">Especifique a opção **raw_interfaces_only** na diretiva **#import**.</span><span class="sxs-lookup"><span data-stu-id="e00d9-111">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="e00d9-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e00d9-112">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="e00d9-113">-ou-</span><span class="sxs-lookup"><span data-stu-id="e00d9-113">-or-</span></span>  
  
- <span data-ttu-id="e00d9-114">Inclua uma diretiva #import para Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="e00d9-114">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="e00d9-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e00d9-115">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e00d9-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e00d9-116">See also</span></span>

- [<span data-ttu-id="e00d9-117">Expondo componentes do .NET Framework para COM</span><span class="sxs-lookup"><span data-stu-id="e00d9-117">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="e00d9-118">Registrando assemblies com o COM</span><span class="sxs-lookup"><span data-stu-id="e00d9-118">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="e00d9-119">[Chamando um objeto .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e00d9-119">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="e00d9-120">[Implantando um aplicativo para acesso COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e00d9-120">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
