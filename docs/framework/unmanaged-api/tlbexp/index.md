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
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="74fcf-102">Funções auxiliares Tlbexp (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="74fcf-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="74fcf-103">O [ferramenta exportador da biblioteca](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) carrega uma biblioteca de vínculo dinâmico chamada TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="74fcf-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="74fcf-104">Essa DLL contém duas funções auxiliares e uma interface que usa a ferramenta de exportação durante o processo de conversão de assembly a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="74fcf-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74fcf-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="74fcf-105">In This Section</span></span>  
 [<span data-ttu-id="74fcf-106">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="74fcf-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="74fcf-107">Fornece informações de localização e o sistema operacional para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="74fcf-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="74fcf-108">Função LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="74fcf-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="74fcf-109">Carrega uma biblioteca de tipos usando uma implementação de [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) para resolver qualquer referenciado bibliotecas de tipo.</span><span class="sxs-lookup"><span data-stu-id="74fcf-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="74fcf-110">Interface ITypeLibResolver</span><span class="sxs-lookup"><span data-stu-id="74fcf-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="74fcf-111">Fornece o [método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), que retorna o caminho totalmente qualificado de uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="74fcf-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
