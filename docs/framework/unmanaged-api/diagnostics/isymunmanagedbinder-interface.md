---
title: Interface ISymUnmanagedBinder
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bbdc4b1f15c8dbb154ed7b967bb21c61d11782a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425546"
---
# <a name="isymunmanagedbinder-interface"></a>Interface ISymUnmanagedBinder
Representa um associador de símbolo para código não gerenciado.  
  
> [!IMPORTANT]
>  É um risco de segurança para abrir um arquivo de programa (PDB) de banco de dados de uma fonte não confiável.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|Dado uma interface de metadados e um nome de arquivo, retorna o correto [ISymUnmanagedReader](isymunmanagedreader-interface.md) estrutura que lerá os símbolos de depuração associados com o módulo.|  
|[Método GetReaderFromStream](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna o correto [ISymUnmanagedReader](isymunmanagedreader-interface.md) símbolos de estrutura que lerá a depuração do armazenamento de símbolo dado.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedBinder2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [Interface ISymUnmanagedBinder3](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
