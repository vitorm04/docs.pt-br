---
title: <section> elemento
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153718"
---
# <a name="section-element"></a>\<elemento> seção

Contém uma declaração de seção de configuração.

[**\<>de configuração**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSeções>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>de seção**

[**\<>de configuração**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSeções>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de sectionGroup**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de seção**

## <a name="syntax"></a>Sintaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Atributos obrigatórios

|           | Descrição |
| --------- | ----------- |
| **name**  | Especifica o nome da seção de configuração. |
| **type**  | Especifica o nome da classe de manipulador de seção de configuração que lê a seção do arquivo de configuração. O valor do tipo tem a sintaxe "totalmente qualificado-se-se-handler-class-name, simples-assembly-name". O nome de montagem simples é o nome do arquivo raiz sem a extensão de arquivo *.dll.* |

## <a name="optional-attributes"></a>Atributos opcionais

Os seguintes atributos são aplicáveis apenas para aplicações ASP.NET. O sistema de configuração ignora esses atributos para outros tipos de aplicativos.

|                     | Descrição |
| ------------------- | ----------- |
| **Allowdefinition** | Especifica em qual arquivo de configuração a seção pode ser usada. Use um dos seguintes valores:<br><br>**Em todo lugar**<br>Permite que a seção seja usada em qualquer arquivo de configuração. Esse é o padrão.<br>**Somente máquina**<br>Permite que a seção seja usada apenas no arquivo de configuração da máquina *(Machine.config*).<br>**Machinetoapplication**<br>Permite que a seção seja usada no arquivo de configuração da máquina ou no arquivo de configuração do aplicativo. |
| **permitirLocalização**   | Determina se a seção pode ser usada dentro do ** \<elemento>de localização.** Use um dos seguintes valores:<br><br>**true**<br>Permite que a seção seja usada dentro do ** \<elemento>de localização.** Esse é o padrão.<br>**false**<br>Não permite que a seção ** \<** seja usada dentro do elemento>localização. |

## <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [** \<configSeções>** Elemento](configsections-element-for-configuration.md) | Contém seção de configuração e declarações de namespace. |
| [>de sectionGroup ** \<** Elemento](sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |

> [!NOTE]
> Uma ** \<seção>** elemento é um elemento filho de ** \<>de configSections ou** ** \<sectionGroup>,** mas não ambos.

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Declarar uma seção de configuração define essencialmente um novo elemento para o arquivo de configuração. O novo elemento contém configurações que um manipulador de seção <xref:System.Configuration.IConfigurationSectionHandler> de configuração (ou seja, uma classe que implementa a interface) lê. Os atributos e elementos filho de uma seção que você define dependem do manipulador de seção que você usa para ler suas configurações.

Declarar um manipulador de seção de configuração no arquivo *Machine.config* permite que você use a seção de configuração em qualquer arquivo de configuração de aplicativo nesse computador, a menos que o atributo **allowDefinition** especifique o contrário.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração e definir configurações para essa seção:

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

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema de arquivo de configuração para o Framework .NET](index.md)
