---
title: Funções auxiliares Tlbexp (referência de API não gerenciada)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: cbde2af9c8a03e6c41f571120027030713f1b8d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104120"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="af524-102">Funções auxiliares Tlbexp (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="af524-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="af524-103">A [ferramenta Exportador da biblioteca de tipos](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) carrega uma biblioteca de vínculo dinâmico chamada TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="af524-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="af524-104">Essa DLL contém duas funções auxiliares e uma interface que a ferramenta de exportação usa durante o processo de conversão de assembly para biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="af524-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af524-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="af524-105">In This Section</span></span>  
 [<span data-ttu-id="af524-106">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="af524-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="af524-107">Fornece informações de localização e do sistema operacional para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="af524-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="af524-108">Função LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="af524-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="af524-109">Carrega uma biblioteca de tipos por meio de uma implementação da [interface ITypeLibResolver](itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipos referenciadas.</span><span class="sxs-lookup"><span data-stu-id="af524-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="af524-110">Interface ITypeLibResolver</span><span class="sxs-lookup"><span data-stu-id="af524-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="af524-111">Fornece o [método ResolveTypeLib](resolvetypelib-method.md), que retorna o caminho totalmente qualificado de uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="af524-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
