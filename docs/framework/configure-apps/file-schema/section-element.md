---
title: <section> Elemento
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c1675540df6844f98572c11cfb140bff23b31a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089025"
---
# <a name="section-element"></a>elemento de > de seção \<

Contém uma declaração de seção de configuração.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<configsections >** ](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<seção >**

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<configsections >** ](configsections-element-for-configuration.md)\
&nbsp;&nbsp;[ **&nbsp;&nbsp;\<o >\** ](sectiongroup-element-for-configsections.md)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**seção**\<

## <a name="syntax"></a>Sintaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Atributos necessários

|           | Descrição |
| --------- | ----------- |
| **name**  | Especifica o nome da seção de configuração. |
| **type**  | Especifica o nome da classe de manipulador da seção de configuração que lê a seção do arquivo de configuração. O valor do tipo tem a sintaxe "totalmente qualificado-section-Handle-Class-Name, Simple-Assembly-Name". O nome do assembly simples é o nome de arquivo raiz sem a extensão de arquivos *. dll* . |

## <a name="optional-attributes"></a>Atributos opcionais

Os atributos a seguir são aplicáveis somente para aplicativos ASP.NET. O sistema de configuração ignora esses atributos para outros tipos de aplicativos.

|                     | Descrição |
| ------------------- | ----------- |
| **allowDefinition** | Especifica em qual arquivo de configuração a seção pode ser usada. Use um dos seguintes valores:<br><br>**Parte**<br>Permite que a seção seja usada em qualquer arquivo de configuração. Esse é o padrão.<br>**MachineOnly**<br>Permite que a seção seja usada somente no arquivo de configuração da máquina (*Machine. config*).<br>**MachineToApplication**<br>Permite que a seção seja usada no arquivo de configuração do computador ou no arquivo de configuração do aplicativo. |
| **allowLocation**   | Determina se a seção pode ser usada dentro do elemento **\<local >** . Use um dos seguintes valores:<br><br>**true**<br>Permite que a seção seja usada dentro do elemento **\<local >** . Esse é o padrão.<br>**false**<br>Não permite que a seção seja usada dentro do elemento **\<local >** . |

## <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [ **\<configsections >** Elementos](configsections-element-for-configuration.md) | Contém as declarações de namespace e seção de configuração. |
| [ **\<> de seção** Elementos](sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |

> [!NOTE]
> Um elemento de **> de seção\<** é um elemento filho de **\<configSections >** ou\<o > de **seção** , mas não ambos.

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Declarar uma seção de configuração essencialmente define um novo elemento para o arquivo de configuração. O novo elemento contém configurações que um manipulador de seção de configuração (ou seja, uma classe que implementa a interface de <xref:System.Configuration.IConfigurationSectionHandler>) lê. Os atributos e os elementos filho de uma seção que você define dependem do manipulador de seção que você usa para ler suas configurações.

A declaração de um manipulador de seção de configuração no arquivo *Machine. config* permite que você use a seção de configuração em qualquer arquivo de configuração de aplicativo nesse computador, a menos que o atributo **AllowDefinition** especifique o contrário.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
