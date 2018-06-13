---
title: Método ICorDebugFunction2::EnumerateNativeCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4d15d9ae63e63f98ab73e250df558dfa16002a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411782"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="7954c-102">Método ICorDebugFunction2::EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="7954c-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="7954c-103">Obtém um ponteiro de interface para um objeto ICorDebugCodeEnum que contém as instruções de código nativo na função referenciada por este objeto ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="7954c-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7954c-104">`EnumerateNativeCode` não é implementado na versão atual do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7954c-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7954c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7954c-105">Syntax</span></span>  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7954c-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7954c-106">Requirements</span></span>  
 <span data-ttu-id="7954c-107">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7954c-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
