---
title: 'Como: Referenciar tipos .NET por meio do COM'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 081548f9004d2fedf4d49845d3f44d4609fa508e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626301"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="cdcf6-102">Como: Referenciar tipos .NET por meio do COM</span><span class="sxs-lookup"><span data-stu-id="cdcf6-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="cdcf6-103">Do ponto de vista do código de cliente e servidor, as diferenças entre o .NET Framework e o COM são bastante invisíveis.</span><span class="sxs-lookup"><span data-stu-id="cdcf6-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="cdcf6-104">Os clientes do Microsoft Visual Basic podem exibir um objeto .NET no Pesquisador de Objetos, que expõe os métodos de objeto e a sintaxe, propriedades e campos exatamente como se fosse qualquer outro objeto COM.</span><span class="sxs-lookup"><span data-stu-id="cdcf6-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="cdcf6-105">O processo de importação de uma biblioteca de tipos é um pouco mais complicado para clientes do C++, embora você use as mesmas ferramentas para exportar metadados para uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="cdcf6-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="cdcf6-106">Para referenciar membros do objeto .NET de um cliente C++ não gerenciado, referencie o arquivo TLB (produzido com Tlbexp.exe) com a diretiva **#import**.</span><span class="sxs-lookup"><span data-stu-id="cdcf6-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="cdcf6-107">Ao referenciar uma biblioteca de tipos C++, você deve especificar a opção **raw_interfaces_only** ou importar as definições na biblioteca de classes base, Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="cdcf6-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="cdcf6-108">Para importar uma biblioteca</span><span class="sxs-lookup"><span data-stu-id="cdcf6-108">To import a library</span></span>  
  
- <span data-ttu-id="cdcf6-109">Especifique a opção **raw_interfaces_only** na diretiva **#import**.</span><span class="sxs-lookup"><span data-stu-id="cdcf6-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="cdcf6-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cdcf6-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="cdcf6-111">- ou -</span><span class="sxs-lookup"><span data-stu-id="cdcf6-111">-or-</span></span>  
  
- <span data-ttu-id="cdcf6-112">Inclua uma diretiva #import para Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="cdcf6-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="cdcf6-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cdcf6-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cdcf6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdcf6-114">See also</span></span>

- [<span data-ttu-id="cdcf6-115">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="cdcf6-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="cdcf6-116">Registrando assemblies usando COM</span><span class="sxs-lookup"><span data-stu-id="cdcf6-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="cdcf6-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)) (Chamando um objeto .NET)</span><span class="sxs-lookup"><span data-stu-id="cdcf6-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="cdcf6-118">[Implantando um aplicativo para acesso COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cdcf6-118">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
