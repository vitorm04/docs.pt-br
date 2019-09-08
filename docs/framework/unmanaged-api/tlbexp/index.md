---
title: Funções auxiliares Tlbexp (referência de API não gerenciada)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a95ff535a4d0847fbd4b8af28f873b67a1829a4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798828"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="3ce67-102">Funções auxiliares Tlbexp (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="3ce67-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="3ce67-103">A [ferramenta Exportador da biblioteca de tipos](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) carrega uma biblioteca de vínculo dinâmico chamada TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="3ce67-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="3ce67-104">Essa DLL contém duas funções auxiliares e uma interface que a ferramenta de exportação usa durante o processo de conversão de assembly para biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="3ce67-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ce67-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3ce67-105">In This Section</span></span>  
 [<span data-ttu-id="3ce67-106">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="3ce67-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="3ce67-107">Fornece informações de localização e do sistema operacional para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="3ce67-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="3ce67-108">Função LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="3ce67-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="3ce67-109">Carrega uma biblioteca de tipos por meio de uma implementação da [interface ITypeLibResolver](itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipos referenciadas.</span><span class="sxs-lookup"><span data-stu-id="3ce67-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="3ce67-110">Interface ITypeLibResolver</span><span class="sxs-lookup"><span data-stu-id="3ce67-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="3ce67-111">Fornece o [método ResolveTypeLib](resolvetypelib-method.md), que retorna o caminho totalmente qualificado de uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="3ce67-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
