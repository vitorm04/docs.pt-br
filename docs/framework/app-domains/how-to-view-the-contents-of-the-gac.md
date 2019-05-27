---
title: 'Como: Exibir o conteúdo do cache de assembly global'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c7d197ea7178abf991247e5ecca02c2b8e94713
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634367"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Como: Exibir o conteúdo do cache de assembly global

Use a [Ferramenta de Cache de Assembly Global (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para exibir o conteúdo do GAC (cache de assembly global).

## <a name="view-the-assemblies-in-the-gac"></a>Exibir os assemblies no GAC

Para exibir uma lista de assemblies no cache de assembly global, abra o [Prompt de Comando do Desenvolvedor para Visual Studio](../tools/developer-command-prompt-for-vs.md) e, em seguida, digite o seguinte comando:

```shell
gacutil -l
```

- ou -

```shell
gacutil /l
```

> [!NOTE]
> Nas versões anteriores do .NET Framework, a extensão do shell do Windows [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) permitia exibir o cache de assembly global no Explorador de Arquivos. A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.

## <a name="see-also"></a>Consulte também

- [Como trabalhar com assemblies e o cache de assembly global](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../tools/gacutil-exe-gac-tool.md)
