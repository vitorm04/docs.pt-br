---
title: "&lt;seção&gt; elemento"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e7de6e5ce6415c58deeca14df74c26e24957054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="section-element"></a>\<seção > elemento

Contém uma declaração de seção de configuração.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<seção >**

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<seção >**

## <a name="syntax"></a>Sintaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Atributos necessários.

|           | Descrição |
| --------- | ----------- |
| **name**  | Especifica o nome da seção de configuração. |
| **type**  | Especifica o nome da classe do manipulador de seção de configuração que lê a seção do arquivo de configuração. O valor do tipo tem a sintaxe "simples de assembly de nome fully-qualified-section-handler-class-name". O nome do assembly simples é o nome do arquivo raiz sem o *. dll* extensão de arquivo. |

## <a name="optional-attributes"></a>Atributos opcionais

Os atributos a seguir são aplicáveis apenas para aplicativos ASP.NET. O sistema de configuração ignorará esses atributos para outros tipos de aplicativos.

|                     | Descrição |
| ------------------- | ----------- |
| **allowDefinition** | Especifica qual arquivo de configuração, a seção pode ser usada em. Use um dos seguintes valores:<br><br>**Em qualquer lugar**<br>Permite que a seção a ser usado em qualquer arquivo de configuração. Esse é o padrão.<br>**MachineOnly**<br>Permite que a seção a ser usado apenas no arquivo de configuração da máquina (*Machine. config*).<br>**MachineToApplication**<br>Permite que a seção a ser usado no arquivo de configuração de máquina ou o arquivo de configuração do aplicativo. |
| **allowLocation**   | Determina se a seção pode ser usada dentro de  **\<local >** elemento. Use um dos seguintes valores:<br><br>**true**<br>Permite que a seção a ser usado dentro de  **\<local >** elemento. Esse é o padrão.<br>**false**<br>Não permite a seção a ser usado dentro de  **\<local >** elemento. |

## <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [**\<configSections >** elemento](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Contém declarações de namespace e de seção de configuração. |
| [**\<sectionGroup >** elemento](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |

> [!NOTE]
> Um  **\<seção >** é um elemento filho do  **\<configSections >** ou  **\<sectionGroup >** , mas não ambos.

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Declarar uma seção de configuração essencialmente define um novo elemento para o arquivo de configuração. O novo elemento contém configurações que uma configuração de manipulador de seção (ou seja, uma classe que implementa o <xref:System.Configuration.IConfigurationSectionHandler> interface) lê. Os atributos e elementos filho de uma seção que você definir dependem do manipulador de seção que você usa para ler as configurações.

Declarando um manipulador de seção de configuração no *Machine. config* arquivo permite que você use a seção de configuração em qualquer arquivo de configuração do aplicativo no computador, a menos que o **allowDefinition**atributo especifique o contrário.

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

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
