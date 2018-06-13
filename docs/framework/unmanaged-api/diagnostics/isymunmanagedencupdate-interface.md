---
title: Interface ISymUnmanagedENCUpdate
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05cbe098b73dd817546dd72f0fc98ad548f75386
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425412"
---
# <a name="isymunmanagedencupdate-interface"></a>Interface ISymUnmanagedENCUpdate
Fornece funções para o recurso Editar e continuar.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetLocalVariableCount](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Obtém o número de variáveis locais.|  
|[Método GetLocalVariables](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Obtém as variáveis locais.|  
|[Método InitializeForEnc](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Permite que os limites de método deve ser calculada antes da primeira chamada para o [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) método.|  
|[Método UpdateMethodLines](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Permite atualizar as informações de linha para um método que não foi recompilado, mas cujas linhas foram movidos independentemente. Um delta para cada instrução é permitida.|  
|[Método UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Permite que um compilador para omitir as funções que não foram modificadas desde o fluxo do programa (PDB) de banco de dados, desde que as informações de linha atende aos requisitos. As informações corretas de linha podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
