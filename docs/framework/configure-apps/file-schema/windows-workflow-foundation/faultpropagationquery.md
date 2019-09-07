---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398726"
---
# <a name="faultpropagationquery"></a>\<faultPropagationQuery>

Representa uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.  Esse evento ocorre toda vez que um FaultHandler processa uma falha. Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade. A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.

 Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> faultPropagationQueries**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> faultPropagationQuery**

## <a name="syntax"></a>Sintaxe

```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|Nome_da_atividade|Uma cadeia de caracteres que especifica o nome da atividade do manipulador de falhas que propagaram a falha. O padrão é *, que indica que os registros de propagação de falha são retornados para todas as atividades.|
|faultHandlerActivityName|Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|Representa uma lista de elementos de configuração que são usados para rastrear a manipulação de falhas que ocorrem dentro de uma atividade.  Esse evento ocorre toda vez que um FaultHandler processa uma falha.|

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Acompanhando perfis](../../../windows-workflow-foundation/tracking-profiles.md)
