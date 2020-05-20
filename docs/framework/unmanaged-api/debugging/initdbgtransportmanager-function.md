---
title: Função InitDbgTransportManager
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: e18ceb25b9c58a9710ef967cb071e3ef55beea8c
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421040"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="77b69-102">Função InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="77b69-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="77b69-103">Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="77b69-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77b69-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="77b69-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="77b69-105">Return Value</span></span>  
 <span data-ttu-id="77b69-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="77b69-106">S_OK</span></span>  
 <span data-ttu-id="77b69-107">Êxito.</span><span class="sxs-lookup"><span data-stu-id="77b69-107">Success.</span></span>  
  
 <span data-ttu-id="77b69-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="77b69-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="77b69-109">A função não pôde alocar memória para um Gerenciador de transporte.</span><span class="sxs-lookup"><span data-stu-id="77b69-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="77b69-110">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="77b69-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="77b69-111">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="77b69-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77b69-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77b69-112">Requirements</span></span>  
 <span data-ttu-id="77b69-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77b69-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77b69-114">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="77b69-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="77b69-115">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="77b69-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="77b69-116">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="77b69-116">**.NET Framework Versions:** 3.5 SP1</span></span>
