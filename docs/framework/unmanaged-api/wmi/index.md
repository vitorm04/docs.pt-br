---
title: "WMI e contadores de desempenho (referência de API não gerenciada)"
description: "Resume o Framework .NET API não gerenciada para informações do contador de desempenho e de WMI."
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.date: 11/06/2017
ms.topic: reference
ms.prod: .net-framework
ms.devlang: cpp
ms.workload:
- dotnet
ms.openlocfilehash: c7959d6b6b7bafd728db5a579ff1376e686c5b74
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Management Instrumentation (WMI) e contadores de desempenho (referência de API não gerenciada)

A API não gerenciada do .NET Framework WMI e contadores de desempenho consiste em um conjunto de funções que envolvem a chamadas para o [API nativa da instrumentação de gerenciamento do Windows](https://msdn.microsoft.com/library/aa389276(v=vs.85).aspx). Ele permite que você desenvolver ferramentas e bibliotecas que gerenciar e monitoram os sistemas de computador remoto.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
A API inclui as seguintes funções:

| Função | Descrição |
|---------|---------|
| [Função BeginEnumeration](beginenumeration.md) | Redefine o enumerador para o início de uma enumeração de propriedades do objeto WMI. |
| [Função BeginMethodEnumeration](beginmethodenumeration.md) |  Inicia uma enumeração dos métodos disponíveis para um objeto. |
| [Função BlessIWbemServices](blessiwbemservices.md) | Indica se as credenciais do usuário permitirem o acesso a uma determinada classe IWbemServices. |
| [Função BlessIWbemServicesObject](blessiwbemservicesobject.md) | Indica se as credenciais do usuário permitirem o acesso a um objeto de serviço IWbem especificado. |
| [Função Clone](clone.md) | Retorna um novo objeto que é um clone completo do objeto atual. |
| [Função CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Faz uma cópia lógica de um enumerador, mantendo sua posição atual em uma enumeração. |
| [Função CompareTo](compareto.md) | Compara a um objeto para outro objeto de gerenciamento do Windows. |
| [Função ConnectServerWmi](connectserverwmi.md) | Cria uma conexão por meio do DCOM para um namespace do WMI em um computador especificado. |
| [Função CreateClassEnumWmi](createclassenumwmi.md) | Retorna um enumerador para todas as classes que atendem aos critérios de seleção especificada. |
| [Função CreateInstanceEnumWmi](createinstanceenumwmi.md) | Retorna um enumerador que retorna as instâncias de uma classe especificada que atendem aos critérios de seleção especificada. |
| [Função Delete](delete.md) | Exclui uma propriedade especificada de uma definição de classe e todos os seus qualificadores. |
| [Função DeleteMethod](deletemethod.md) | Exclui um método especificado de uma definição de classe do CIM. |
| [Função EndEnumeration](endenumeration.md) | Encerra uma sequência de enumeração. | 
| [Função EndMethodEnumeration](endmethodenumeration.md) | Encerra uma sequência de enumeração iniciada chamando o [BeginMethodEnumeration função](beginmethodenumeration.md). |
| [Função ExecNotificationQueryWmi](execnotificationquerywmi.md) | Executa uma consulta para receber eventos. |
| [Função ExecQueryWmi](execquerywmi.md) | Executa uma consulta para recuperar objetos. |
| [Função FormatFromRawValue](formatfromrawvalue.md) | Converte um valor de dados de desempenho bruto para o formato especificado ou dois valores de dados de desempenho bruto se a conversão de formato é baseado no tempo. | 
| [Função Get](get.md) | Recupera um valor de propriedade especificado se ele existir. |
| [Função GetCurrentApartmentType](getcurrentapartmenttype.md) | Recupera o tipo do compartimento em que o chamador está em execução. |
| [Função GetDemultiplexedStub](getdemultiplexedstub.md) | Cria um coletor do encaminhador de objeto para ajudar um cliente receber chamadas assíncronas de gerenciamento do Windows. |
| [Função GetErrorInfo](geterrorinfo.md) | Recupera informações de erro na chamada de função anterior. | 
| [Função GetMethod](getmethod.md) | Recupera informações sobre o método especificado. | 
| [Função GetMethodOrigin](getmethodorigin.md) | Determina a classe em que um método é declarado. |
| [Função GetMethodQualifierSet](getmethodqualifierset.md) | Recupera o qualificador definido para um método específico. |
| [Função GetNames](getnames.md) | Recupera um subconjunto ou todos os nomes das propriedades de um objeto. |
| [Função GetObjectText](getobjecttext.md) | Retorna um processamento textual de um objeto na sintaxe MOF. | 
| [Função GetPropertyHandle](getpropertyhandle.md) | Retorna um identificador exclusivo que identifica uma propriedade. |
| [Função GetPropertyOrigin](getpropertyorigin.md) | Determina a classe na qual uma propriedade é declarada. |
| [Função GetPropertyQualifierSet](getpropertyqualifierset.md) | Recupera o qualificador definido para uma determinada propriedade.  |
| [Função GetQualifierSet](getqualifierset.md) | Recupera o qualificador definido para uma instância da classe ou uma definição de classe. |
| [Função InheritsFrom](inheritsfrom.md) | Determina se a classe ou instância atual é derivada de uma classe pai especificada. |
| [Função Initialize](initialize.md) | Executa a inicialização do WMI. |
| [Função Next](next.md) | Recupera a próxima propriedade em uma enumeração. | 
| [Função NextMethod](nextmethod.md) | Recupera o próximo método em uma enumeração. |
| [Colocar a função](put.md) | Define uma propriedade nomeada para um novo valor. |
| [Função PutClassWmi](putclasswmi.md) | Cria uma nova classe ou atualiza uma existente. |
| [Função PutInstanceWmi](putinstancewmi.md) | Cria ou atualiza uma instância de uma classe existente. A instância é gravada no repositório do WMI. |
| [Função PutMethod](putmethod.md) | Cria um método. |
| [Função QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) | Redefine um enumerador de qualificadores de um objeto para o início da enumeração. |
| [Função QualifierSet_Delete](qualifierset-delete.md) | Exclui um qualificador especificado por nome.  |
| [Função QualifierSet_EndEnumeration](qualifierset-endenumeration.md) | Finaliza a enumeração iniciada com uma chamada para o `QualifierSet_BeginEnumeration` função. |
| [Função QualifierSet_Get](qualifierset-get.md) | Obtém o qualificador nomeado especificado.  |
| [Função QualifierSet_GetNames](qualifierset-getnames.md) | Recupera os nomes de todos os qualificadores ou qualificadores especificado que estão disponíveis do objeto atual ou propriedade. |
| [Função QualifierSet_Next](qualifierset-next.md) | Recupera o próximo qualificador em uma enumeração que foi iniciado com uma chamada para o [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) função. |
| [Função QualifierSet_Put](qualifierset-put.md) | Grava o qualificador de nome e o valor. |
| [Função ResetSecurity](resetsecurity.md) | Atribui o token de representação fornecido para o thread atual. |
| [Função SetSecurity](setsecurity.md) | Recupera o token de representação associado ao segmento atual. |
| [Função SpawnDerivedClass](spawnderivedclass.md) | Cria um objeto de classe derivada recentemente de um objeto especificado. | 
| [Função SpawnInstance](spawninstance.md) | Cria uma nova instância de uma classe. |   
| [Função VerifyClient](verifyclientkey.md) | Garante que a chave do cliente tem a segurança correta. |
| [Função WritePropertyValue](writepropertyvalue.md) | Grava um número especificado de bytes em uma propriedade identificada por um identificador de propriedade. |

 ## <a name="see-also"></a>Consulte também
[Referência de API não gerenciada](../index.md) 
