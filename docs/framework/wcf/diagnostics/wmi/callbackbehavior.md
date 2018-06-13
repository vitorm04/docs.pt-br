---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2755ac4f365536366b41e743110ce494063a5ecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486928"
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe CallbackBehavior não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe CallbackBehavior tem as seguintes propriedades:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Quando for verdadeiro, a sessão é fechada automaticamente quando um serviço fecha uma sessão duplex.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Tipo de dados: cadeia de caracteres  
Tipo de acesso: somente leitura  
  
 Especifica se o serviço oferece suporte a um thread, vários threads ou chamadas reentrantes.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que especifica se deve enviar dados de serialização desconhecidos na conexão.  
  
### <a name="includeexceptiondetailinfaults"></a>includeExceptionDetailInFaults  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Quando habilitada, detalhes sobre exceções no retorno de chamada são anexados às falhas retornadas ao serviço.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de itens permitidos em um objeto serializado.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se deve usar o contexto de sincronização atual para escolher o thread de execução.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se o sistema ou o aplicativo reforça o processamento de cabeçalho MustUnderstand SOAP.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
