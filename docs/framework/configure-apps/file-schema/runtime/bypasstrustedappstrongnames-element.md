---
title: Elemento <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35b4c6201b5181b8d7241906f60a731e4175d523
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991232"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<Elemento bypassTrustedAppStrongNames>

Especifica se deve ignorar a validação de nomes fortes em assemblies de confiança total que são carregados em uma confiança <xref:System.AppDomain>total.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a>Sintaxe

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o recurso de bypass que evita a validação de nomes fortes para assemblies de confiança total está habilitado. Quando esse recurso é habilitado, nomes fortes não são validados quanto à exatidão quando o assembly é carregado. O padrão é `true`.|

## <a name="enabled-attribute"></a>Atributo habilitado

|Valor|Descrição|
|-----------|-----------------|
|`true`|As assinaturas de nome forte em assemblies de confiança total não são validadas quando os assemblies são carregados em uma confiança <xref:System.AppDomain>total. Esse é o padrão.|
|`false`|As assinaturas de nome forte em assemblies de confiança total são validadas quando os assemblies são carregados em uma confiança <xref:System.AppDomain>total. A assinatura de nome forte é verificada apenas quanto à exatidão da assinatura; Ela não é comparada com outro nome forte para uma correspondência.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

O recurso de bypass de nome forte evita a sobrecarga de verificação de assinatura de nome forte de assemblies de confiança total.

O recurso de desvio se aplica a qualquer assembly que está assinado com um nome forte e que tem as seguintes características:

- Totalmente confiável sem a <xref:System.Security.Policy.StrongName> evidência (por exemplo, tem `MyComputer` evidências de zona).

- Carregado em um <xref:System.AppDomain> totalmente confiável.

- Carregado de um local sob a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> desse <xref:System.AppDomain>.

- Não assinado com atraso.

> [!NOTE]
> Se o recurso de bypass tiver sido desativado para todos os aplicativos no computador usando uma chave do registro, essa configuração do arquivo de configuração não terá nenhum efeito. Para obter mais informações, confira [Como: desabilitar a funcionalidade de bypass de nome forte](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar o comportamento que valida a assinatura de nome forte em assemblies de confiança total.

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Como: Desabilitar o recurso de bypass de nome forte](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
