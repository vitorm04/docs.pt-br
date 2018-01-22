---
title: "Método ResolveTypeLib"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72d1cedbfc1a1ec6c3588a7b0be9cf657d7369fd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="resolvetypelib-method"></a>Método ResolveTypeLib
Resolve o nome simple de uma biblioteca de tipos, retornando o caminho totalmente qualificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bstrSimpleName`  
 [in] Um [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) que contém o nome simple da biblioteca de tipos.  
  
 `tlbid`  
 [in] O GUID atribuído à biblioteca de tipos no registro.  
  
 `lcid`  
 [in] A identificação da localização da biblioteca de tipos.  
  
 `wMajorVersion`  
 [in] O número de versão principal da biblioteca de tipos. Por exemplo, para versão *x. y*, o número de versão principal é *x*.  
  
 `wMinorVersion`  
 [in] O número de versão secundária da biblioteca de tipos. Por exemplo, para versão *x. y*, é o número de versão secundária *y*.  
  
 `syskind`  
 [in] Um [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) sinalizador que identifica o ambiente operacional. Os valores comuns são SYS_WIN32 e SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 [out] Um ponteiro para um [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.  
  
## <a name="remarks"></a>Comentários  
 O `ResolveTypeLib` método é chamado pelo [função LoadTypeLibWithResolver](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) durante [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) de processamento.  
  
 Implementações personalizadas dessa interface devem retornar um [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** TlbRef.idl, TlbRef.h  
  
 **Biblioteca:** TlbRef.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções auxiliares do Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
