---
title: Elemento <assemblyBinding> para <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155473"
---
# <a name="assemblybinding-element-for-configuration"></a>\<montagemElemento de \<> de vinculação para> de configuração

Especifica a diretiva de ligação de assembly no nível de configuração.

configuração &nbsp; &nbsp; [** \<>**](configuration-element.md) ** \<montagem>vinculante**

## <a name="syntax"></a>Sintaxe

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **xmlns** | Atributo obrigatório.<br><br>Especifica o espaço de nome XML necessário para a vinculação do conjunto. Use a string "urna:schemas-microsoft-com:asm.v1" como valor. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<>de configuração**](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-element"></a>Elemento filho

|     | Descrição |
| --- | ----------- |
| [**\<>de configuração de linked**](linkedconfiguration-element.md) | Especifica um arquivo de configuração a ser incluído. |

## <a name="remarks"></a>Comentários

O elemento [** \<linkedConfiguration>**](linkedconfiguration-element.md) simplifica o gerenciamento de conjuntos de componentes, permitindo que os arquivos de configuração de aplicativos incluam arquivos de configuração de montagem em locais conhecidos, em vez de duplicar configurações de configuração de montagem.

> [!NOTE]
> O elemento ** \<linkedConfiguration>** não é suportado para aplicativos com manifestos lado a lado do Windows.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como incluir um arquivo de configuração no disco rígido local:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Confira também

- [Esquema de arquivo de configuração para o Framework .NET](index.md)
