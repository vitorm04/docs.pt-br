---
title: Enumeração CorSymSearchPolicyAttributes
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178344"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="a77fb-102">Enumeração CorSymSearchPolicyAttributes</span><span class="sxs-lookup"><span data-stu-id="a77fb-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="a77fb-103">Especifica a diretiva a ser usada ao fazer uma pesquisa por um leitor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="a77fb-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="a77fb-104">Essas constantes são usadas pelos [métodos ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) e [ISymUnmanagedBinder3::GetReaderFromCallback.](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)</span><span class="sxs-lookup"><span data-stu-id="a77fb-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a77fb-105">É um risco de segurança abrir um arquivo de banco de dados de programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="a77fb-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77fb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a77fb-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="a77fb-107">Membros</span><span class="sxs-lookup"><span data-stu-id="a77fb-107">Members</span></span>  
  
|<span data-ttu-id="a77fb-108">Membro</span><span class="sxs-lookup"><span data-stu-id="a77fb-108">Member</span></span>|<span data-ttu-id="a77fb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a77fb-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="a77fb-110">Consulta o registro de caminhos de pesquisa de símbolos.</span><span class="sxs-lookup"><span data-stu-id="a77fb-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="a77fb-111">Acessa um servidor símbolo.</span><span class="sxs-lookup"><span data-stu-id="a77fb-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="a77fb-112">Pesquisa o caminho especificado no diretório Debug.</span><span class="sxs-lookup"><span data-stu-id="a77fb-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="a77fb-113">Procura o PDB no local onde está o arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="a77fb-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a77fb-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a77fb-114">Requirements</span></span>  
 <span data-ttu-id="a77fb-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a77fb-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77fb-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a77fb-116">See also</span></span>

- [<span data-ttu-id="a77fb-117">Enumerações de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="a77fb-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
