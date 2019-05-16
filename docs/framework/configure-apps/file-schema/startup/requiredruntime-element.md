---
title: Elemento <requiredRuntime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: f5a9f99133c153401694372abaeea10a02e492e5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634187"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime > elemento

Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Esse elemento foi preterido e não deve mais ser usado. O [ `supportedRuntime` ](supportedruntime-element.md) elemento deve ser usado em vez disso.

\<configuration> \<startup> \<requiredRuntime>

## <a name="syntax"></a>Sintaxe

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`version`|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a versão do .NET Framework que oferece suporte a esse aplicativo. O valor de cadeia de caracteres deve corresponder ao nome de diretório encontrado na raiz de instalação do .NET Framework. O conteúdo do valor de cadeia de caracteres não é analisado.|
|`safemode`|Atributo opcional.<br /><br /> Especifica se o código de inicialização de tempo de execução procura o registro para determinar a versão de tempo de execução.|

## <a name="safemode-attribute"></a>atributo de modo de segurança

|Valor|Descrição|
|-----------|-----------------|
|`false`|O código de inicialização de tempo de execução examina o registro. Este é o valor padrão.|
|`true`|O código de inicialização de tempo de execução não parece no registro.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`startup`|Contém o `<requiredRuntime>` elemento.|

## <a name="remarks"></a>Comentários
 Os aplicativos criados para oferecer suporte somente à versão 1.0 do tempo de execução devem usar o `<requiredRuntime>` elemento. Aplicativos criados usando a versão 1.1 ou posterior do tempo de execução devem usar o `<supportedRuntime>` elemento.

> [!NOTE]
> Se você usar o [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração de função, você deve usar o `<requiredRuntime>` elemento para todas as versões do tempo de execução. O `<supportedRuntime>` elemento é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 O `version` cadeia de caracteres do atributo deve corresponder ao nome de pasta de instalação para a versão especificada do .NET Framework. Essa cadeia de caracteres não é interpretada. Se o código de inicialização de tempo de execução não encontrar uma pasta correspondente, o tempo de execução não será carregado; o código de inicialização mostra uma mensagem de erro e o fecha.

> [!NOTE]
> O código de inicialização para um aplicativo que está hospedado no Microsoft Internet Explorer ignorará o `<requiredRuntime>` elemento.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Esquema de configurações de inicialização](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
