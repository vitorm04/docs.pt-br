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
ms.openlocfilehash: 2d67bee3ea0e57080179b3fbb7e0b4193860c44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103282"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="67ae8-102">Função InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="67ae8-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="67ae8-103">Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="67ae8-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ae8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67ae8-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="67ae8-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="67ae8-105">Return Value</span></span>  
 <span data-ttu-id="67ae8-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="67ae8-106">S_OK</span></span>  
 <span data-ttu-id="67ae8-107">Êxito.</span><span class="sxs-lookup"><span data-stu-id="67ae8-107">Success.</span></span>  
  
 <span data-ttu-id="67ae8-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="67ae8-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="67ae8-109">A função não pôde alocar memória para um Gerenciador de transporte.</span><span class="sxs-lookup"><span data-stu-id="67ae8-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="67ae8-110">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="67ae8-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="67ae8-111">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="67ae8-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ae8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67ae8-112">Requirements</span></span>  
 <span data-ttu-id="67ae8-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ae8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ae8-114">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="67ae8-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="67ae8-115">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="67ae8-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="67ae8-116">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="67ae8-116">**.NET Framework Versions:** 3.5 SP1</span></span>
