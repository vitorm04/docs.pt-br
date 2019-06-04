---
title: Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59565b28991f6d61ff2c6c77540eace92461aa89
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490176"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="cc7a2-102">Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="cc7a2-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="cc7a2-103">Aponta para uma função que notifica o host quando um sobreposta (ou seja, assíncrona) e/s para um dispositivo foi concluída.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="cc7a2-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7a2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc7a2-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc7a2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc7a2-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="cc7a2-107">[in] Um valor que é um código de erro se o dispositivo foi fechado; Caso contrário, esse valor é zero.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="cc7a2-108">Fechar um dispositivo faz com que todas as pendentes de e/s para o dispositivo para ser concluída imediatamente.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="cc7a2-109">[in] O número de bytes transferidos pela operação de e/s.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="cc7a2-110">[in] Um ponteiro para uma estrutura que contém as informações a serem usadas para concluir a solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc7a2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc7a2-111">Remarks</span></span>  
 <span data-ttu-id="cc7a2-112">A função à qual `LPOVERLAPPED_COMPLETION_ROUTINE` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="cc7a2-113">A função de retorno de chamada permite que o host processar a solicitação de e/s concluída.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7a2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc7a2-114">Requirements</span></span>  
 <span data-ttu-id="cc7a2-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7a2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7a2-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc7a2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc7a2-117">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="cc7a2-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="cc7a2-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7a2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc7a2-119">See also</span></span>

- [<span data-ttu-id="cc7a2-120">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="cc7a2-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
