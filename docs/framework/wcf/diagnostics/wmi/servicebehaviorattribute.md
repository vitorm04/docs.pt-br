---
title: ServiceBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6b0620e9cb2575bcfe9cd6f01b5d87669df69b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceBehaviorAttribute não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceBehaviorAttribute tem as seguintes propriedades:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se fechar automaticamente uma sessão quando um cliente fechar uma sessão de saída.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Tipo de dados: cadeia de caracteres  
Tipo de acesso: somente leitura  
  
 Indica se um serviço oferece suporte a um thread, vários threads ou chamadas reentrantes.  
  
### <a name="configurationname"></a>ConfigurationName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome da configuração do serviço.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se deve enviar dados de serialização desconhecidos na conexão.  
  
### <a name="includeexceptiondetailinfaults"></a>includeExceptionDetailInFaults  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.  
  
### <a name="instancecontextmode"></a>InstanceContextMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Especifica quando um novo objeto de serviço é criado.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de itens permitidos em um objeto serializado.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O atributo de nome do serviço em WSDL.  
  
### <a name="namespace"></a>Namespace  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O namespace de destino do serviço em WSDL.  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se o objeto de serviço será reciclado quando a transação atual seja concluída.  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se as transações pendentes a são concluídos quando fecha a sessão atual.  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Especifica o nível de isolamento da transação.  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O período no qual uma transação deve ser concluída.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se deve usar o contexto de sincronização atual para escolher a execução de thread.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se o sistema ou o aplicativo reforça o processamento de cabeçalho MustUnderstand SOAP.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
