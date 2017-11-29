---
title: "Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPOVERLAPPED_COMPLETION_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords: LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d50f2058796d4c5c900474cdcbe71d8a5a911ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="5bb2b-102">Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="5bb2b-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="5bb2b-103">Aponta para uma função que notifica o host quando um sobreposto (ou seja, assíncrona) e/s para um dispositivo foi concluída.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="5bb2b-104">Este ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5bb2b-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bb2b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5bb2b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5bb2b-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="5bb2b-107">[in] Um valor que é um código de erro se o dispositivo foi fechado; Caso contrário, esse valor é zero.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="5bb2b-108">Fechar um dispositivo faz com que todas as pendentes de e/s para o dispositivo para ser concluída imediatamente.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="5bb2b-109">[in] O número de bytes transferidos pela operação de e/s.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="5bb2b-110">[in] Um ponteiro para uma estrutura que contém as informações a serem usadas para concluir a solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bb2b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bb2b-111">Remarks</span></span>  
 <span data-ttu-id="5bb2b-112">A função à qual `LPOVERLAPPED_COMPLETION_ROUTINE` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="5bb2b-113">A função de retorno de chamada permite que o host processar a solicitação de e/s concluída.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bb2b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bb2b-114">Requirements</span></span>  
 <span data-ttu-id="5bb2b-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bb2b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bb2b-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5bb2b-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bb2b-117">**Biblioteca:** arquivo MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="5bb2b-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="5bb2b-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bb2b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb2b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bb2b-119">See Also</span></span>  
 [<span data-ttu-id="5bb2b-120">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="5bb2b-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
