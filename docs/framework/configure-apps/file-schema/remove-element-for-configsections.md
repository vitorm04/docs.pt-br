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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154524"
---
# <a name="remove-element-for-configsections"></a>\<remover> \<elemento para configuraçõesSeções>

Remove uma seção ou grupo de seção predefinido.

[**\<>de configuração**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSeções>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remover>**

## <a name="syntax"></a>Sintaxe

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **name**  | Atributo obrigatório.<br><br>Especifica o nome da seção ou do grupo de seção a ser removido. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [** \<configSeções>** Elemento](configsections-element-for-configuration.md) | Contém seção de configuração e declarações de namespace. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

Você pode ** \<** usar o elemento remove>para remover seções e grupos de seção do seu aplicativo que foram definidos em um nível mais alto na hierarquia do arquivo de configuração.

## <a name="example"></a>Exemplo

O exemplo a seguir ** \<** mostra como usar o elemento remove>em um arquivo de configuração de aplicativo para remover uma seção previamente definida no arquivo de configuração da máquina.

O código de arquivo de configuração da máquina a seguir declara a amostra da ** \<seçãoSection>**:

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

O código de arquivo de configuração do aplicativo a seguir remove a ** \<seção sampleSection>.** Após a remoção, o aplicativo não pode recuperar as configurações em ** \<sampleSes>**.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema de arquivo de configuração para o Framework .NET](index.md)
