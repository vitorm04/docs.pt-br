---
title: Expondo componentes do COM para o .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4472adf2c309803d4d5ac57f3522cc260782d85
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833666"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="5722d-102">Expondo componentes do COM para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5722d-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="5722d-103">Esta seção resume o processo necessário para expor um componente COM existente ao código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5722d-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="5722d-104">Para obter detalhes sobre como escrever servidores COM que são totalmente integrados ao .NET Framework, consulte [Considerações sobre design para interoperação](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5722d-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="5722d-105">Os componentes COM existentes são recursos valiosos no código gerenciado, como aplicativos de negócios de camada intermediária ou como uma funcionalidade isolada.</span><span class="sxs-lookup"><span data-stu-id="5722d-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="5722d-106">Um componente ideal tem um assembly de interoperabilidade primário e está em conformidade total com os padrões de programação impostos pelo COM.</span><span class="sxs-lookup"><span data-stu-id="5722d-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="5722d-107">Para expor componentes COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5722d-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="5722d-108">[Importe uma biblioteca de tipos como um assembly](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="5722d-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="5722d-109">O Common Language Runtime exige metadados para todos os tipos, incluindo tipos COM.</span><span class="sxs-lookup"><span data-stu-id="5722d-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="5722d-110">Há várias maneiras de obter um assembly que contém tipos COM importados como metadados.</span><span class="sxs-lookup"><span data-stu-id="5722d-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="5722d-111">[Use tipos COM em código gerenciado](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5722d-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="5722d-112">É possível inspecionar tipos COM, ativar instâncias e invocar métodos no objeto COM da mesma maneira que você faria com qualquer tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5722d-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="5722d-113">[Compile um projeto de interoperabilidade](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="5722d-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="5722d-114">O SDK (Software Development Kit) do Windows fornece compiladores para várias linguagens em conformidade com a CLS (Common Language Specification), incluindo Visual Basic, C# e C++.</span><span class="sxs-lookup"><span data-stu-id="5722d-114">The Windows Software Development Kit (SDK) provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="5722d-115">[Implante um aplicativo de interoperabilidade](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="5722d-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="5722d-116">Os aplicativos de interoperabilidade são mais bem implantados como assemblies assinados [de nome forte](../app-domains/strong-named-assemblies.md) no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="5722d-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5722d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5722d-117">See also</span></span>

- [<span data-ttu-id="5722d-118">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="5722d-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="5722d-119">[Considerações sobre design para interoperação](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5722d-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="5722d-120">Amostra de interoperabilidade COM: cliente .NET e servidor COM</span><span class="sxs-lookup"><span data-stu-id="5722d-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="5722d-121">Componentes de independência de linguagem e componentes independentes da linguagem</span><span class="sxs-lookup"><span data-stu-id="5722d-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="5722d-122">Gacutil.exe (Ferramenta do Cache de Assemblies Global)</span><span class="sxs-lookup"><span data-stu-id="5722d-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
