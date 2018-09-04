---
title: WMI e Contadores de Desempenho (Referência de API Não Gerenciada)
description: Resume a API não gerenciada do .NET Framework para informações do contador de desempenho e de WMI.
author: rpetrusha
ms.author: ronpet
ms.date: 11/06/2017
ms.openlocfilehash: 6e105bc28b6011c3177216aba996eb85c0766ac8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407871"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>WMI (Instrumentação de Gerenciamento do Windows) e Contadores de Desempenho (Referência de API Não Gerenciada)

A API não gerenciada dos Contadores de Desempenho e da WMI do .NET Framework consistem em um conjunto de funções que encapsulam chamadas para a [API nativa da Instrumentação de Gerenciamento do Windows](/windows/desktop/WmiSdk/com-api-for-wmi). Ela permite que você desenvolva as ferramentas e as bibliotecas que gerenciam e monitoram os sistemas de computador remoto.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
A API inclui as seguintes funções:

| Função | Descrição |
|---------|---------|
| [Função BeginEnumeration](beginenumeration.md) | Redefine o enumerador para o início da enumeração das propriedades de objeto da WMI. |
| [Função BeginMethodEnumeration](beginmethodenumeration.md) |  Inicia uma enumeração dos métodos disponíveis para um objeto. |
| [Função BlessIWbemServices](blessiwbemservices.md) | Indica se as credenciais de usuário permitem o acesso a uma classe IWbemServices especificada. |
| [Função BlessIWbemServicesObject](blessiwbemservicesobject.md) | Indica se as credenciais de usuário permitem o acesso a um objeto de serviço IWbemServices especificado. |
| [Função Clone](clone.md) | Retorna um novo objeto que é uma cópia completa do objeto atual. |
| [Função CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Faz uma cópia lógica de um enumerador, mantendo sua posição atual em uma enumeração. |
| [Função CompareTo](compareto.md) | Compara um objeto a outro objeto de gerenciamento do Windows. |
| [Função ConnectServerWmi](connectserverwmi.md) | Cria uma conexão por meio do DCOM para um namespace do WMI em um computador especificado. |
| [Função CreateClassEnumWmi](createclassenumwmi.md) | Retorna um enumerador para todas as classes que satisfaçam os critérios de seleção especificados. |
| [Função CreateInstanceEnumWmi](createinstanceenumwmi.md) | Retorna um enumerador que retorna as instâncias de uma classe especificada que atendem aos critérios de seleção especificados. |
| [Função Delete](delete.md) | Exclui uma propriedade especificada de uma definição de classe e todos seus qualificadores. |
| [Função DeleteMethod](deletemethod.md) | Exclui um método especificado de uma definição de classe do CIM. |
| [Função EndEnumeration](endenumeration.md) | Encerra uma sequência de enumeração. | 
| [Função EndMethodEnumeration](endmethodenumeration.md) | Encerra uma sequência de enumeração iniciada ao chamar a [função BeginMethodEnumeration](beginmethodenumeration.md). |
| [Função ExecNotificationQueryWmi](execnotificationquerywmi.md) | Executa uma consulta para receber eventos. |
| [Função ExecQueryWmi](execquerywmi.md) | Executa uma consulta para recuperar objetos. |
| [Função FormatFromRawValue](formatfromrawvalue.md) | Converte um valor de dados de desempenho brutos para o formato especificado, ou dois valores de dados de desempenho brutos se a conversão de formato é baseada em tempo. | 
| [Função Get](get.md) | Recupera um valor da propriedade especificado, caso exista. |
| [Função GetCurrentApartmentType](getcurrentapartmenttype.md) | Recupera o tipo de apartment no qual o chamador está sendo executado. |
| [Função GetDemultiplexedStub](getdemultiplexedstub.md) | Cria um coletor do encaminhador de objeto para ajudar um cliente a receber chamadas assíncronas do Gerenciamento do Windows. |
| [Função GetErrorInfo](geterrorinfo.md) | Recupera informações de erro da chamada de função anterior. | 
| [Função GetMethod](getmethod.md) | Recupera informações sobre o método especifico. | 
| [Função GetMethodOrigin](getmethodorigin.md) | Determina a classe na qual um método é declarado. |
| [Função GetMethodQualifierSet](getmethodqualifierset.md) | Recupera o qualificador definido para um método específico. |
| [Função GetNames](getnames.md) | Recupera um subconjunto ou todos os nomes das propriedades de um objeto. |
| [Função GetObjectText](getobjecttext.md) | Retorna uma renderização textual de um objeto na sintaxe MOF. | 
| [Função GetPropertyHandle](getpropertyhandle.md) | Retorna um identificador exclusivo que reconhece uma propriedade. |
| [Função GetPropertyOrigin](getpropertyorigin.md) | Determina a classe na qual uma propriedade é declarada. |
| [Função GetPropertyQualifierSet](getpropertyqualifierset.md) | Recupera o qualificador definido para uma propriedade específica.  |
| [Função GetQualifierSet](getqualifierset.md) | Recupera o qualificador definido para uma instância da classe ou uma definição de classe. |
| [Função InheritsFrom](inheritsfrom.md) | Determina se a classe ou instância atual é derivada de uma classe pai especificada. |
| [Função Initialize](initialize.md) | Executa a inicialização do WMI. |
| [Função Next](next.md) | Recupera a próxima propriedade em uma enumeração. | 
| [Função NextMethod](nextmethod.md) | Recupera o próximo método em uma enumeração. |
| [Função Put](put.md) | Define uma propriedade nomeada para um novo valor. |
| [Função PutClassWmi](putclasswmi.md) | Cria uma nova classe ou atualiza uma existente. |
| [Função PutInstanceWmi](putinstancewmi.md) | Cria ou atualiza uma instância de uma classe existente. A instância é gravada no repositório da WMI. |
| [Função PutMethod](putmethod.md) | Cria um método. |
| [Função QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) | Redefine um enumerador dos qualificadores de um objeto para o início da enumeração. |
| [Função QualifierSet_Delete](qualifierset-delete.md) | Exclui um qualificador especificado por nome.  |
| [Função QualifierSet_EndEnumeration](qualifierset-endenumeration.md) | Finaliza a enumeração iniciada com uma chamada para a função `QualifierSet_BeginEnumeration`. |
| [Função QualifierSet_Get](qualifierset-get.md) | Obtém o qualificador nomeado especificado.  |
| [Função QualifierSet_GetNames](qualifierset-getnames.md) | Recupera os nomes de todos os qualificadores ou de qualificadores especificados que estão disponíveis por meio do objeto atual ou da propriedade. |
| [Função QualifierSet_Next](qualifierset-next.md) | Recupera o próximo qualificador em uma enumeração que começou com uma chamada para a função [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
| [Função QualifierSet_Put](qualifierset-put.md) | Grava o qualificador nomeado e o valor. |
| [Função ResetSecurity](resetsecurity.md) | Atribui o token de representação fornecido para o thread atual. |
| [Função SetSecurity](setsecurity.md) | Recupera o token de representação associado ao thread atual. |
| [Função SpawnDerivedClass](spawnderivedclass.md) | Cria um objeto de classe derivada recentemente por meio de um objeto especificado. | 
| [Função SpawnInstance](spawninstance.md) | Cria uma nova instância de uma classe. |   
| [Função VerifyClient](verifyclientkey.md) | Garante que a chave do cliente tenha a segurança correta. |
| [Função WritePropertyValue](writepropertyvalue.md) | Grava um número especificado de bytes em uma propriedade identificada por um identificador de propriedade. |

 ## <a name="see-also"></a>Consulte também
[Referência de API não gerenciada](../index.md) 
