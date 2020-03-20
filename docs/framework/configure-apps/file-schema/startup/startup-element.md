---
title: Elemento <startup>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153719"
---
# <a name="startup-element"></a>\<elemento> de inicialização

Especifica informações comuns de inicialização em tempo de execução do idioma.

[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;**\<>de startup**  

## <a name="syntax"></a>Sintaxe

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|Atributo opcional.<br /><br /> Especifica se habilita a política de ativação de tempo de execução .NET Framework 2.0 ou se usa a política de ativação do .NET Framework 4.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>usarLegacyV2ExecutartempoA atribuiçãoPolítica de diretivadeativação

|Valor|Descrição|
|-----------|-----------------|
|`true`|Habilitar a política de ativação de tempo de execução .NET Framework 2.0 para o tempo de execução escolhido, que é vincular técnicas de ativação de tempo de execução legados (como a [função CorBindToRuntimeEx)](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)ao tempo de execução escolhido no arquivo de configuração em vez de capping-los na versão 2.0 CLR. Assim, se a versão 4 ou posterior clr for escolhida a partir do arquivo de configuração, conjuntos de modo misto criados com versões anteriores do .NET Framework são carregados com a versão CLR escolhida. A definição desse valor impede que a versão 1.1 ou a versão CLR 2.0 seja carregada no mesmo processo, desabilitando efetivamente o recurso lado a lado no processo.|
|`false`|Use a política de ativação padrão para o .NET Framework 4 e posterior, que é permitir que técnicas de ativação de tempo de execução legados carreguem a versão CLR 1.1 ou 2.0 no processo. A definição desse valor impede que conjuntos de modos mistos sejam carregados no Quadro .NET 4 ou posterior, a menos que tenham sido construídos com o Quadro .NET 4 ou posterior. Esse valor é o padrão.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[\<>de tempo de execução obrigatório](requiredruntime-element.md)|Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Os aplicativos construídos com a versão 1.1 ou posterior em tempo de execução devem usar o ** \<elemento de>runtime suportado.**|
|[\<>de runtime suportado](supportedruntime-element.md)|Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|

## <a name="remarks"></a>Comentários

 O elemento ** \<de>runtime suportado** deve ser usado por todos os aplicativos construídos usando a versão 1.1 ou posterior do tempo de execução. Os aplicativos construídos para suportar apenas a versão 1.0 do tempo de execução devem usar o ** \<elemento requiredRuntime>.**

 O código de inicialização de um aplicativo ** \<** hospedado no Microsoft Internet Explorer ignora o elemento de>inicial e seus elementos infantis.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>O atributo UseLegacyV2RuntimeActivationPolicy

 Esse atributo é útil se o aplicativo usar caminhos de ativação legados, como a [função CorBindToRuntimeEx,](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)e você deseja que esses caminhos ativem a versão 4 da CLR em vez de uma versão anterior, ou se seu aplicativo for construído com o .NET Framework 4, mas tiver uma dependência de um conjunto de modo misto construído com uma versão anterior do .NET Framework. Nesses cenários, defina `true`o atributo para .

> [!NOTE]
> Definir o `true` atributo para impedir que a versão CLR 1.1 ou a versão CLR 2.0 seja carregada no mesmo processo, desabilitando efetivamente o recurso lado a lado no processo (consulte [Execução lado a lado para COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como especificar a versão em tempo de execução em um arquivo de configuração.

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Confira também

- [Esquema de configurações de inicialização](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Como: Configurar um aplicativo para suportar versões .NET Framework 4 ou posteriores](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Execução lado a lado para interoperabilidade COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Execução lado a lado em processo](../../../deployment/in-process-side-by-side-execution.md)
