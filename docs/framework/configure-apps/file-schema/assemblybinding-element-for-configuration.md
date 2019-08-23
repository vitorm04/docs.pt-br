---
title: Elemento <assemblyBinding> para <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921268"
---
# <a name="assemblybinding-element-for-configuration"></a>\<elemento de > assemblyBinding \<para > de configuração

Especifica a diretiva de ligação de assembly no nível de configuração.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<assemblyBinding>**

## <a name="syntax"></a>Sintaxe

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **xmlns** | Atributo obrigatório.<br><br>Especifica o namespace XML necessário para a associação de assembly. Use a cadeia de caracteres "urn: schemas-microsoft-com: asm. v1" como o valor. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-element"></a>Elemento filho

|     | Descrição |
| --- | ----------- |
| [ **\<linkedConfiguration>** ](linkedconfiguration-element.md) | Especifica um arquivo de configuração a ser incluído. |

## <a name="remarks"></a>Comentários

O elemento > linkedConfiguration simplifica o gerenciamento de assemblies de componente, permitindo que os arquivos de configuração de aplicativo incluam arquivos de configuração de assembly em locais bem conhecidos, em vez de duplicar o assembly [ **\<** ](linkedconfiguration-element.md) definições de configuração.

> [!NOTE]
> O elemento de  **\<> linkedConfiguration** não tem suporte para aplicativos com manifestos lado a lado do Windows.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como incluir um arquivo de configuração no disco rígido local:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
