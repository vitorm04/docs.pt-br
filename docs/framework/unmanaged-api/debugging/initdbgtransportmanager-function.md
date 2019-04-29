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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761644"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="d8b81-102">Função InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="d8b81-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="d8b81-103">Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d8b81-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8b81-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d8b81-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8b81-105">Return Value</span></span>  
 <span data-ttu-id="d8b81-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8b81-106">S_OK</span></span>  
 <span data-ttu-id="d8b81-107">Êxito.</span><span class="sxs-lookup"><span data-stu-id="d8b81-107">Success.</span></span>  
  
 <span data-ttu-id="d8b81-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d8b81-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="d8b81-109">A função não pôde alocar memória para um Gerenciador de transporte.</span><span class="sxs-lookup"><span data-stu-id="d8b81-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="d8b81-110">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="d8b81-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d8b81-111">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="d8b81-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8b81-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8b81-112">Requirements</span></span>  
 <span data-ttu-id="d8b81-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8b81-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b81-114">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="d8b81-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d8b81-115">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="d8b81-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d8b81-116">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d8b81-116">**.NET Framework Versions:** 3.5 SP1</span></span>
