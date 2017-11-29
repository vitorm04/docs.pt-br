---
title: "Função InitDbgTransportManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: InitDbgTransportManager
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f9f637589666af3723f11eb1f828d00be57793e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="d5a53-102">Função InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="d5a53-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="d5a53-103">Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d5a53-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5a53-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d5a53-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5a53-105">Return Value</span></span>  
 <span data-ttu-id="d5a53-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5a53-106">S_OK</span></span>  
 <span data-ttu-id="d5a53-107">Êxito.</span><span class="sxs-lookup"><span data-stu-id="d5a53-107">Success.</span></span>  
  
 <span data-ttu-id="d5a53-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d5a53-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="d5a53-109">A função não pôde alocar memória para um Gerenciador de transporte.</span><span class="sxs-lookup"><span data-stu-id="d5a53-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="d5a53-110">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="d5a53-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d5a53-111">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="d5a53-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5a53-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5a53-112">Requirements</span></span>  
 <span data-ttu-id="d5a53-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a53-114">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="d5a53-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d5a53-115">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="d5a53-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d5a53-116">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d5a53-116">**.NET Framework Versions:** 3.5 SP1</span></span>
