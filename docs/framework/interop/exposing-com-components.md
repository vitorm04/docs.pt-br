---
title: Expondo componentes do COM para o .NET Framework
description: Conheça o processo de exposição de componentes COM ao .NET. Os componentes COM são valiosos em código gerenciado como aplicativos de negócios de camada intermediária ou funcionalidade isolada.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 34dda58d9513874169927164706fafdd95e8ed84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554176"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="98d5e-104">Expondo componentes do COM para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="98d5e-104">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="98d5e-105">Esta seção resume o processo necessário para expor um componente COM existente ao código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="98d5e-105">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="98d5e-106">Para obter detalhes sobre como escrever servidores COM que são totalmente integrados ao .NET Framework, consulte [Considerações sobre design para interoperação](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="98d5e-106">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="98d5e-107">Os componentes COM existentes são recursos valiosos no código gerenciado, como aplicativos de negócios de camada intermediária ou como uma funcionalidade isolada.</span><span class="sxs-lookup"><span data-stu-id="98d5e-107">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="98d5e-108">Um componente ideal tem um assembly de interoperabilidade primário e está em conformidade total com os padrões de programação impostos pelo COM.</span><span class="sxs-lookup"><span data-stu-id="98d5e-108">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="98d5e-109">Para expor componentes COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="98d5e-109">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="98d5e-110">[Importe uma biblioteca de tipos como um assembly](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="98d5e-110">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="98d5e-111">O Common Language Runtime exige metadados para todos os tipos, incluindo tipos COM.</span><span class="sxs-lookup"><span data-stu-id="98d5e-111">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="98d5e-112">Há várias maneiras de obter um assembly que contém tipos COM importados como metadados.</span><span class="sxs-lookup"><span data-stu-id="98d5e-112">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="98d5e-113">[Use tipos COM em código gerenciado](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="98d5e-113">[Use COM types in managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="98d5e-114">É possível inspecionar tipos COM, ativar instâncias e invocar métodos no objeto COM da mesma maneira que você faria com qualquer tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="98d5e-114">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="98d5e-115">[Compile um projeto de interoperabilidade](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="98d5e-115">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="98d5e-116">O SDK do Windows fornece compiladores para várias linguagens em conformidade com CLS (Common Language Specification), incluindo Visual Basic, C# e C++.</span><span class="sxs-lookup"><span data-stu-id="98d5e-116">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="98d5e-117">[Implante um aplicativo de interoperabilidade](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="98d5e-117">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="98d5e-118">Os aplicativos de interoperabilidade são mais bem implantados como assemblies assinados [de nome forte](../../standard/assembly/strong-named.md) no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="98d5e-118">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d5e-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="98d5e-119">See also</span></span>

- [<span data-ttu-id="98d5e-120">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="98d5e-120">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="98d5e-121">[Considerações sobre design para interoperação](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="98d5e-121">[Design Considerations for Interoperation](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="98d5e-122">Exemplo de interoperabilidade COM: cliente .NET e servidor COM</span><span class="sxs-lookup"><span data-stu-id="98d5e-122">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="98d5e-123">Componentes de independência de linguagem e componentes independentes da linguagem</span><span class="sxs-lookup"><span data-stu-id="98d5e-123">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="98d5e-124">Gacutil.exe (Ferramenta de Cache de Assembly Global)</span><span class="sxs-lookup"><span data-stu-id="98d5e-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
