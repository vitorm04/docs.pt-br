---
title: Como referenciar tipos do .NET com base no COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 345a698a4d45093dfb873a8303712a7bff5046cd
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="a6c62-102">Como referenciar tipos do .NET com base no COM</span><span class="sxs-lookup"><span data-stu-id="a6c62-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="a6c62-103">Do ponto de vista do código de cliente e servidor, as diferenças entre o .NET Framework e o COM são bastante invisíveis.</span><span class="sxs-lookup"><span data-stu-id="a6c62-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="a6c62-104">Os clientes do Microsoft Visual Basic podem exibir um objeto .NET no Pesquisador de Objetos, que expõe os métodos de objeto e a sintaxe, propriedades e campos exatamente como se fosse qualquer outro objeto COM.</span><span class="sxs-lookup"><span data-stu-id="a6c62-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="a6c62-105">O processo de importação de uma biblioteca de tipos é um pouco mais complicado para clientes do C++, embora você use as mesmas ferramentas para exportar metadados para uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="a6c62-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="a6c62-106">Para referenciar membros do objeto .NET de um cliente C++ não gerenciado, referencie o arquivo TLB (produzido com Tlbexp.exe) com a diretiva **#import**.</span><span class="sxs-lookup"><span data-stu-id="a6c62-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="a6c62-107">Ao referenciar uma biblioteca de tipos C++, você deve especificar a opção **raw_interfaces_only** ou importar as definições na biblioteca de classes base, Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="a6c62-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="a6c62-108">Para importar uma biblioteca</span><span class="sxs-lookup"><span data-stu-id="a6c62-108">To import a library</span></span>  
  
-   <span data-ttu-id="a6c62-109">Especifique a opção **raw_interfaces_only** na diretiva **#import**.</span><span class="sxs-lookup"><span data-stu-id="a6c62-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="a6c62-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6c62-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="a6c62-111">-ou-</span><span class="sxs-lookup"><span data-stu-id="a6c62-111">-or-</span></span>  
  
-   <span data-ttu-id="a6c62-112">Inclua uma diretiva #import para Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="a6c62-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="a6c62-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6c62-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a6c62-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6c62-114">See Also</span></span>  
 <span data-ttu-id="a6c62-115">[Expondo componentes do .NET Framework para COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) </span><span class="sxs-lookup"><span data-stu-id="a6c62-115">[Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) </span></span>  
 <span data-ttu-id="a6c62-116">[Registrando assemblies usando COM](../../../docs/framework/interop/registering-assemblies-with-com.md) </span><span class="sxs-lookup"><span data-stu-id="a6c62-116">[Registering Assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md) </span></span>  
 <span data-ttu-id="a6c62-117">[Chamando um objeto .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33) </span><span class="sxs-lookup"><span data-stu-id="a6c62-117">[Calling a .NET Object](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33) </span></span>  
 [<span data-ttu-id="a6c62-118">Implantando um aplicativo para acesso COM</span><span class="sxs-lookup"><span data-stu-id="a6c62-118">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)

