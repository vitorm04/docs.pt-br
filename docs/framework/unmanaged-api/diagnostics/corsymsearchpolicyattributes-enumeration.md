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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a9b0f085820bac12638c0310ab23b2eafacb23b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986499"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="9cbe9-102">Enumeração CorSymSearchPolicyAttributes</span><span class="sxs-lookup"><span data-stu-id="9cbe9-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="9cbe9-103">Especifica a política a ser usado ao fazer uma pesquisa por um leitor de símbolo.</span><span class="sxs-lookup"><span data-stu-id="9cbe9-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="9cbe9-104">Essas constantes são usadas pelo [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) e [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="9cbe9-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9cbe9-105">É um risco de segurança para abrir um arquivo de programa (PDB) do banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="9cbe9-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cbe9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9cbe9-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="9cbe9-107">Membros</span><span class="sxs-lookup"><span data-stu-id="9cbe9-107">Members</span></span>  
  
|<span data-ttu-id="9cbe9-108">Membro</span><span class="sxs-lookup"><span data-stu-id="9cbe9-108">Member</span></span>|<span data-ttu-id="9cbe9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cbe9-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="9cbe9-110">Consulta o registro para caminhos de pesquisa do símbolo.</span><span class="sxs-lookup"><span data-stu-id="9cbe9-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="9cbe9-111">Acessa um servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="9cbe9-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="9cbe9-112">Pesquisa o caminho especificado no diretório de depuração.</span><span class="sxs-lookup"><span data-stu-id="9cbe9-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="9cbe9-113">Pesquisa o PDB no local onde está o arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="9cbe9-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cbe9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cbe9-114">Requirements</span></span>  
 <span data-ttu-id="9cbe9-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9cbe9-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbe9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cbe9-116">See also</span></span>

- [<span data-ttu-id="9cbe9-117">Enumerações do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="9cbe9-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
