---
title: Função GetCORSystemDirectory
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 137b2e30916cb1934d4389c5668bfb7eb5066064
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617224"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="81a81-102">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="81a81-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="81a81-103">Retorna o diretório de instalação do Common Language Runtime (CLR) que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="81a81-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="81a81-104">O diretório de instalação é totalmente qualificado, por exemplo, "c:\Windows\Microsoft.NET\Framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="81a81-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="81a81-105">Esta função é preterida.</span><span class="sxs-lookup"><span data-stu-id="81a81-105">This function is deprecated.</span></span> <span data-ttu-id="81a81-106">Ele é substituído pelo método [ICLRRuntimeInfo:: GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) fornecido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="81a81-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a81-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81a81-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="81a81-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81a81-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="81a81-109">fora Um buffer no qual o tempo de execução retorna uma cadeia de caracteres que contém o nome totalmente qualificado do diretório de instalação para o tempo de execução que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="81a81-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="81a81-110">Se o tempo de execução ainda não tiver sido carregado no processo, a função retornará as informações de diretório apropriadas para a versão mais recente do tempo de execução instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="81a81-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="81a81-111">no O tamanho, em bytes, de `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="81a81-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="81a81-112">fora O número de caracteres retornados em `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="81a81-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81a81-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="81a81-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="81a81-114">Não use essa função em processos que estejam executando a versão 4 do CLR.</span><span class="sxs-lookup"><span data-stu-id="81a81-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="81a81-115">Se uma versão anterior do CLR estiver instalada no computador, essa função retornará o diretório de instalação para essa versão.</span><span class="sxs-lookup"><span data-stu-id="81a81-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a81-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81a81-116">Requirements</span></span>  
 <span data-ttu-id="81a81-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81a81-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a81-118">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81a81-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81a81-119">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81a81-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81a81-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a81-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a81-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="81a81-121">See also</span></span>

- [<span data-ttu-id="81a81-122">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="81a81-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
