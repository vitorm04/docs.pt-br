---
title: Função LoadLibraryShim
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fe1ba15f8a9f8ee79582158209049c1e502a61d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352512"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="d3d49-102">Função LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="d3d49-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="d3d49-103">Carrega uma versão especificada de uma DLL que está incluída no pacote redistribuível do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3d49-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="d3d49-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3d49-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="d3d49-105">Use o [iclrruntimeinfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d3d49-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d49-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3d49-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3d49-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3d49-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="d3d49-108">[in] Uma cadeia terminada em zero que representa o nome da DLL a ser carregado na biblioteca do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3d49-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="d3d49-109">[in] Uma cadeia terminada em zero que representa a versão da DLL a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="d3d49-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="d3d49-110">Se `szVersion` for nula, a versão selecionada para o carregamento é a versão mais recente da DLL especificado que é inferior à versão 4.</span><span class="sxs-lookup"><span data-stu-id="d3d49-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="d3d49-111">Ou seja, todas as versões iguais ou maiores que a versão 4 são ignoradas se `szVersion` for nulo, e se nenhuma versão menor do que a versão 4 está instalado, a DLL não será carregada.</span><span class="sxs-lookup"><span data-stu-id="d3d49-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="d3d49-112">Isso é para garantir a instalação do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] não afeta componentes ou aplicativos já existentes.</span><span class="sxs-lookup"><span data-stu-id="d3d49-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="d3d49-113">Consulte a entrada [in-proc SxS e o início rápido da migração](https://go.microsoft.com/fwlink/?LinkId=200329) no blog da equipe do CLR.</span><span class="sxs-lookup"><span data-stu-id="d3d49-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d3d49-114">Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="d3d49-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="d3d49-115">[out] Um ponteiro para a alça do módulo.</span><span class="sxs-lookup"><span data-stu-id="d3d49-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3d49-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d3d49-116">Return Value</span></span>  
 <span data-ttu-id="d3d49-117">Esse método retorna códigos de erro padrão (COM Component Object Model), conforme definido em Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3d49-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="d3d49-118">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="d3d49-118">Return code</span></span>|<span data-ttu-id="d3d49-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3d49-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d3d49-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3d49-120">S_OK</span></span>|<span data-ttu-id="d3d49-121">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d3d49-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="d3d49-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="d3d49-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="d3d49-123">Carregando `szDllName` requer o carregamento, o common language runtime (CLR) e a versão necessária do CLR não podem ser carregado.</span><span class="sxs-lookup"><span data-stu-id="d3d49-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3d49-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3d49-124">Remarks</span></span>  
 <span data-ttu-id="d3d49-125">Essa função é usada para carregar as DLLs que são incluídas no pacote redistribuível do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3d49-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="d3d49-126">Ele não carrega DLLs gerados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d3d49-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3d49-127">Começando com o .NET Framework versão 2.0, carregar Fusion faz com que o CLR a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="d3d49-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="d3d49-128">Isso ocorre porque as funções em Fusion agora são wrappers cujas implementações são fornecidas pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d3d49-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3d49-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3d49-129">Requirements</span></span>  
 <span data-ttu-id="d3d49-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d49-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d49-131">**Cabeçalho:** mscoree. H</span><span class="sxs-lookup"><span data-stu-id="d3d49-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3d49-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d49-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d49-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3d49-133">See Also</span></span>  
 [<span data-ttu-id="d3d49-134">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="d3d49-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
