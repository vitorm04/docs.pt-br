---
title: Elemento <remove> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154524"
---
# <a name="remove-element-for-configsections"></a>Elemento \<remove> para \<configSections>

Remove uma seção ou um grupo de seções predefinido.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Sintaxe

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **name**  | Atributo obrigatório.<br><br>Especifica o nome da seção ou do grupo de seções a ser removido. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<configSections>** Elementos](configsections-element-for-configuration.md) | Contém as declarações de namespace e seção de configuração. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Você pode usar o **\<remove>** elemento para remover seções e grupos de seções do seu aplicativo que foram definidos em um nível superior na hierarquia do arquivo de configuração.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar o **\<remove>** elemento em um arquivo de configuração de aplicativo para remover uma seção definida anteriormente no arquivo de configuração da máquina.

O código do arquivo de configuração do computador a seguir declara a seção **\<sampleSection>** :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

O código do arquivo de configuração de aplicativo a seguir remove a **\<sampleSection>** seção. Após a remoção, o aplicativo não pode recuperar as configurações no **\<sampleSection>** .

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
