---
title: 'Método ICorDebugMergedAssemblyRecord:: GetPublicKeyToken'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 4cd0ff788401a7b5d70e215209194c0eb6cad1f8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212107"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="44960-102">Método ICorDebugMergedAssemblyRecord:: GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="44960-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="44960-103">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="44960-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44960-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44960-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44960-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44960-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="44960-106">no O número máximo de bytes na `pbPublicKeyToken` matriz.</span><span class="sxs-lookup"><span data-stu-id="44960-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="44960-107">fora Um ponteiro para o número real de bytes gravados na `pbPublicKeyToken` matriz.</span><span class="sxs-lookup"><span data-stu-id="44960-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="44960-108">fora Um ponteiro para uma matriz de bytes que contém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="44960-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44960-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="44960-109">Remarks</span></span>  
 <span data-ttu-id="44960-110">O token de chave pública de um assembly são os últimos oito bytes de um hash SHA1 de sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="44960-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44960-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="44960-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44960-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44960-112">Requirements</span></span>  
 <span data-ttu-id="44960-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44960-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44960-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44960-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44960-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44960-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44960-116">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44960-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44960-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="44960-117">See also</span></span>

- [<span data-ttu-id="44960-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="44960-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="44960-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="44960-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
