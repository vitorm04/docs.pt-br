---
title: Elemento <remove> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0fcdb75aa733a9d7634ec1c3b31dcbbb87e090e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088729"
---
# <a name="remove-element-for-appsettings"></a>\<remover > elemento para \<appSettings >

Remove as configurações de aplicativo personalizadas.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<remover >**

## <a name="syntax"></a>Sintaxe

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Atributo

|         | Descrição |
| ------- | ----------- |
| **key** | Atributo obrigatório.<br><br>Especifica o nome da chave a ser removida. |

### <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](../index.md)
