---
title: "Funções auxiliares Tlbexp (referência de API não gerenciada)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5d0a0b08be725a50442a3db9f9942bceea7cf8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="6ac73-102">Funções auxiliares Tlbexp (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="6ac73-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="6ac73-103">O [ferramenta exportador da biblioteca](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) carrega uma biblioteca de vínculo dinâmico chamada TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="6ac73-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="6ac73-104">Essa DLL contém duas funções auxiliares e uma interface que usa a ferramenta de exportação durante o processo de conversão de assembly a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="6ac73-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ac73-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6ac73-105">In This Section</span></span>  
 [<span data-ttu-id="6ac73-106">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="6ac73-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="6ac73-107">Fornece informações de localização e o sistema operacional para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="6ac73-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="6ac73-108">Função LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="6ac73-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="6ac73-109">Carrega uma biblioteca de tipos usando uma implementação de [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) para resolver qualquer referenciado bibliotecas de tipo.</span><span class="sxs-lookup"><span data-stu-id="6ac73-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="6ac73-110">Interface ITypeLibResolver</span><span class="sxs-lookup"><span data-stu-id="6ac73-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="6ac73-111">Fornece o [método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), que retorna o caminho totalmente qualificado de uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="6ac73-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
