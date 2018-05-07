---
title: Função InitDbgTransportManager
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="initdbgtransportmanager-function"></a>Função InitDbgTransportManager
Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e o tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 Êxito.  
  
 E_OUTOFMEMORY  
 A função não pôde alocar memória para um Gerenciador de transporte.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Outras falhas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET framework:** 3.5 SP1
