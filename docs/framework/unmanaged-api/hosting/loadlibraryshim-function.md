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
ms.openlocfilehash: 9ab44ce8f51620d83084d1dd16e98b2b310feb76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968931"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="34879-102">Função LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="34879-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="34879-103">Carrega uma versão especificada de uma DLL que está incluída no pacote redistribuível .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34879-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="34879-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="34879-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="34879-105">Em vez disso, use o método [ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) .</span><span class="sxs-lookup"><span data-stu-id="34879-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34879-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34879-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34879-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34879-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="34879-108">no Uma cadeia de caracteres terminada em zero que representa o nome da DLL a ser carregada a partir da biblioteca de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34879-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="34879-109">no Uma cadeia de caracteres terminada em zero que representa a versão da DLL a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="34879-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="34879-110">Se `szVersion` for NULL, a versão selecionada para carregamento será a versão mais recente da DLL especificada menor que a versão 4.</span><span class="sxs-lookup"><span data-stu-id="34879-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="34879-111">Ou seja, todas as versões iguais ou maiores que a versão 4 são ignoradas se `szVersion` for NULL e, se nenhuma versão anterior à versão 4 estiver instalada, a dll não será carregada.</span><span class="sxs-lookup"><span data-stu-id="34879-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="34879-112">Isso é para garantir que a instalação do .NET Framework 4 não afete aplicativos ou componentes pré-existentes.</span><span class="sxs-lookup"><span data-stu-id="34879-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="34879-113">Consulte a entrada [SxS e início rápido de migração](https://go.microsoft.com/fwlink/?LinkId=200329) no blog da equipe do CLR.</span><span class="sxs-lookup"><span data-stu-id="34879-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="34879-114">Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="34879-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="34879-115">fora Um ponteiro para o identificador do módulo.</span><span class="sxs-lookup"><span data-stu-id="34879-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34879-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="34879-116">Return Value</span></span>  
 <span data-ttu-id="34879-117">Esse método retorna códigos de erro padrão de Component Object Model (COM), conforme definido no WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="34879-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="34879-118">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="34879-118">Return code</span></span>|<span data-ttu-id="34879-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="34879-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="34879-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="34879-120">S_OK</span></span>|<span data-ttu-id="34879-121">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="34879-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="34879-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="34879-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="34879-123">O `szDllName` carregamento requer o carregamento do Common Language Runtime (CLR) e a versão necessária do CLR não pode ser carregada.</span><span class="sxs-lookup"><span data-stu-id="34879-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34879-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="34879-124">Remarks</span></span>  
 <span data-ttu-id="34879-125">Essa função é usada para carregar DLLs incluídas no pacote redistribuível .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34879-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="34879-126">Ele não carrega DLLs geradas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="34879-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34879-127">A partir do .NET Framework versão 2,0, o carregamento de Fusion. dll faz com que o CLR seja carregado.</span><span class="sxs-lookup"><span data-stu-id="34879-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="34879-128">Isso ocorre porque as funções em Fusion. dll agora são wrappers cujas implementações são fornecidas pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="34879-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34879-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34879-129">Requirements</span></span>  
 <span data-ttu-id="34879-130">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34879-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34879-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34879-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34879-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34879-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34879-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34879-133">See also</span></span>

- [<span data-ttu-id="34879-134">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="34879-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
