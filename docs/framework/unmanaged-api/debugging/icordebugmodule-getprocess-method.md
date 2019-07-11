---
title: Método ICorDebugModule::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff7c77a27e9be58e9702c3a5e3f990863dc83901
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763629"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="6bd49-102">Método ICorDebugModule::GetProcess</span><span class="sxs-lookup"><span data-stu-id="6bd49-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="6bd49-103">Obtém o processo que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="6bd49-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bd49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bd49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bd49-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="6bd49-106">[out] Um ponteiro para o endereço de um objeto ICorDebugProcess que representa o processo que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="6bd49-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bd49-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bd49-107">Requirements</span></span>  
 <span data-ttu-id="6bd49-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bd49-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd49-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bd49-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bd49-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bd49-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bd49-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd49-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
