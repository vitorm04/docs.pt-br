---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 9d8f4335c304d164daafeb0ad4de5b4e3bba4590
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963950"
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
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
 A classe CallbackBehavior não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe CallbackBehavior tem as seguintes propriedades:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Quando for verdadeiro, a sessão é fechada automaticamente quando um serviço fecha uma sessão duplex.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Tipo de dados: cadeia de caracteres  
Tipo de acesso: Somente leitura  
  
 Especifica se o serviço dá suporte a um thread, vários threads ou chamadas reentrantes.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que especifica se é necessário enviar dados de serialização desconhecidos em trânsito.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Quando habilitado, detalhes sobre exceções no retorno de chamada são anexados às falhas retornadas para o serviço.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 O número máximo de itens permitidos em um objeto serializado.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Especifica se deve usar o contexto de sincronização atual para escolher o thread de execução.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Especifica se o sistema ou o aplicativo impõe o processamento do cabeçalho SOAP MustUnderstand.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
