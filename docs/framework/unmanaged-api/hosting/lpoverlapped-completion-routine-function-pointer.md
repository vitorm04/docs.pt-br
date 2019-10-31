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
ms.openlocfilehash: 103ac75e7c3eaf9739c3a448ff1c052c158621db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090900"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="6faf4-102">Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="6faf4-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="6faf4-103">Aponta para uma função que notifica o host quando uma e/s sobreposta (ou seja, assíncrona) para um dispositivo for concluída.</span><span class="sxs-lookup"><span data-stu-id="6faf4-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="6faf4-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6faf4-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6faf4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6faf4-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6faf4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6faf4-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="6faf4-107">no Um valor que é um código de erro se o dispositivo tiver sido fechado; caso contrário, esse valor será zero.</span><span class="sxs-lookup"><span data-stu-id="6faf4-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="6faf4-108">Fechar um dispositivo faz com que todas as e/s pendentes para o dispositivo sejam concluídas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="6faf4-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="6faf4-109">no O número de bytes transferidos pela operação de e/s.</span><span class="sxs-lookup"><span data-stu-id="6faf4-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="6faf4-110">no Um ponteiro para uma estrutura que contém informações a serem usadas para concluir a solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="6faf4-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6faf4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6faf4-111">Remarks</span></span>  
 <span data-ttu-id="6faf4-112">A função à qual os pontos de `LPOVERLAPPED_COMPLETION_ROUTINE` é uma função de retorno de chamada e deve ser implementada pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="6faf4-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="6faf4-113">A função de retorno de chamada permite que o host processe a solicitação de e/s concluída.</span><span class="sxs-lookup"><span data-stu-id="6faf4-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6faf4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6faf4-114">Requirements</span></span>  
 <span data-ttu-id="6faf4-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6faf4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6faf4-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6faf4-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6faf4-117">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="6faf4-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="6faf4-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6faf4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6faf4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6faf4-119">See also</span></span>

- [<span data-ttu-id="6faf4-120">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="6faf4-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
