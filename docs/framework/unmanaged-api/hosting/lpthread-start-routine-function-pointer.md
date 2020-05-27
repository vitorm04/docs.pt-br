---
title: Ponteiro de função LPTHREAD_START_ROUTINE
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: 84cdb42b11ad70f54f21ae36ca2734dc794d06d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008463"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="f7afd-102">Ponteiro de função LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="f7afd-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="f7afd-103">Aponta para uma função que notifica o host que um thread começou a ser executado.</span><span class="sxs-lookup"><span data-stu-id="f7afd-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="f7afd-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f7afd-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7afd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7afd-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7afd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7afd-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="f7afd-107">no Um ponteiro para o código que iniciou a execução.</span><span class="sxs-lookup"><span data-stu-id="f7afd-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7afd-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7afd-108">Remarks</span></span>  
 <span data-ttu-id="f7afd-109">A função para a qual os `LPTHREAD_START_ROUTINE` pontos é uma função de retorno de chamada e deve ser implementada pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="f7afd-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7afd-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7afd-110">Requirements</span></span>  
 <span data-ttu-id="f7afd-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7afd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7afd-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f7afd-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7afd-113">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="f7afd-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f7afd-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7afd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7afd-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="f7afd-115">See also</span></span>

- [<span data-ttu-id="f7afd-116">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="f7afd-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
