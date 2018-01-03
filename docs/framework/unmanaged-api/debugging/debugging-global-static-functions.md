---
title: "Depurando funções estáticas globais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7fde0941959619f4832019806401be0ffddb81e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-global-static-functions"></a>Depurando funções estáticas globais
Esta seção descreve as funções estáticas globais não gerenciadas que usa a API de depuração.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função _EFN_GetManagedExcepStack](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Fornecido um endereço de objeto de exceção gerenciado, retorna uma versão de cadeia de caracteres de rastreamento de pilha contido.  
  
 [Função _EFN_GetManagedObjectFieldInfo](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Obtém o deslocamento do início de um objeto para um campo e o valor do campo, usando o ponteiro de objeto fornecido e o nome do campo.  
  
 [Função _EFN_GetManagedObjectName](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Obtém o nome de um tipo usando o ponteiro de objeto gerenciado fornecido.  
  
 [Função _EFN_StackTrace](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Fornece uma representação de texto de um rastreamento de pilha gerenciada e uma matriz de `CONTEXT` registra, uma para cada transição entre não gerenciados e código gerenciado.  
  
 [Função CLRDataCreateInstance](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Chamado pelos common language runtime (CLR) dados serviços de acesso para criar o objeto de interface especificada para o processo de destino especificado.  
  
 [Ponteiro de função PFN_CLRDataCreateInstance](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Aponta para uma função que é chamado pelos dados do CLR acessar os serviços para criar o objeto de interface especificada para o processo de destino especificado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
