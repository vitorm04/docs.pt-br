---
title: Interface ISymUnmanagedBinder2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29501eeb6085dbc235112d98e8099fcfa4565000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427789"
---
# <a name="isymunmanagedbinder2-interface"></a>Interface ISymUnmanagedBinder2
Representa um associador de símbolo para código não gerenciado e estende o [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.  
  
> [!IMPORTANT]
>  É um risco de segurança para abrir um arquivo de programa (PDB) de banco de dados de uma fonte não confiável.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|Dado uma interface de metadados e um nome de arquivo, retorna o correto <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface que lerá os símbolos de depuração associados com o módulo. Fornece uma pesquisa mais ampla que o [Isymunmanagedbinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) método.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [Interface ISymUnmanagedBinder3](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
