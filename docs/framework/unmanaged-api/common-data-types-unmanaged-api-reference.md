---
title: Tipos de dados comuns (referência API não gerenciada)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c359c9b14452e82b7fd2425409b373ead430d3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407073"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Tipos de dados comuns (referência API não gerenciada)
Este tópico lista tipos de dados simples usados pelas APIs não gerenciadas para o .NET Framework que são definidas por instruções `typedef` do C/C++. Esses tipos de dados são geralmente aliases para tipos de dados primitivos do C/C++. Geralmente, os valores desses tipos de dados são opacos, ou seja, eles são retornados por uma função ou um método específico para que possam ser transmitidos para outras funções ou métodos sem modificação.  
  
|Tipo de dados|Definição|Definido em|Descrição|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|O identificador de um domínio de aplicativo.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|O identificador de um assembly.|  
|ClassID|`typedef UINT_PTR ClassID;`|corprof.h|O identificador de uma classe gerenciada.|  
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|O identificador de conexão para um thread que está conectado a uma instância do Microsoft SQL Server.|  
|ContextID|`typedef UINT_PTR ContextID;`|corprof.h|O identificador do contexto associado a um thread gerenciado específico.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Um identificador opaco que representa informações sobre um registro de ativação específico.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Um identificador opaco que aponta para um registro de ativação. Ele é válido somente durante o retorno de chamada para o qual é transmitido.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Um endereço na memória.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|O status de continuação.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|O valor de um registro da CPU.|  
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|O identificador de uma função ou um método.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Um identificador da coleta de lixo.|  
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Um token de metadados (uma linha em uma tabela de metadados).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|O identificador de um módulo de assembly.|  
|ObjectID|`typedef UINT_PTR ObjectID;`|corprof.h|O identificador de um objeto.|  
|ProcessID|`typedef UINT_PTR ProcessID;`|corprof.h|O identificador de um processo gerenciado.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|O identificador de uma função com compilação JIT.|  
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|O identificador de um [ICLRTask](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância.|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|O identificador de um thread gerenciado.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API não gerenciada](../../../docs/framework/unmanaged-api/index.md)
