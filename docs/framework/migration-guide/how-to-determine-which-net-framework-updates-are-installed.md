---
title: Consulte atualizações de segurança e hotfixes do .NET Framework instalados
description: Saiba como determinar quais atualizações de segurança e hotfixes do .NET Framework estão instaladas em um computador.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181275"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Como determinar quais atualizações de segurança e hotfixes do .NET Framework estão instalados

Este artigo mostra como descobrir quais atualizações de segurança e hotfixes do .NET Framework estão instaladas em um computador.

> [!NOTE]
> Todas as técnicas mostradas neste artigo exigem uma conta com privilégios administrativos.

## <a name="use-registry-editor"></a>Use o Editor de Registro

As atualizações de segurança e os hotfixes instalados para cada versão do .NET Framework instalado em um computador estão listadas no Registro do Windows. Você pode usar o programa Editor do Registro (*regedit.exe*) para exibir essas informações.

1. Abra o programa **regedit.exe**. Nas versões Windows 8 e posteriores, clique com o botão direito do mouse **Start** ![Screenshot do logotipo da chave do Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Logotipo do Windowskeyboard")e selecione **Executar**. Na caixa **Abrir**, digite **regedit.exe** e selecione **OK**.

2. No Editor do Registro, abrir a seguinte subchave:

     **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**

     As atualizações instaladas estão listadas nas subchaves que identificam a versão do .NET Framework a que se aplicam. Cada atualização é identificada por um número da Base de Dados de Conhecimento (KB).

No Editor do Registro, as versões do .NET Framework e as atualizações instaladas para cada versão são armazenadas em subchaves diferentes. Para saber mais sobre como detectar os números da versão instalada, veja [Como determinar quais versões do .NET Framework estão instaladas](how-to-determine-which-versions-are-installed.md).

## <a name="query-the-registry-using-code"></a>Consultar o registro usando código

O exemplo a seguir determina programaticamente as atualizações de segurança e os hotfixes do .NET Framework que estão instalados em um computador:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

O exemplo produz uma saída semelhante à seguinte:

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="use-powershell-to-query-the-registry"></a>Use o PowerShell para consultar o registro

O exemplo a seguir mostra como determinar as atualizações de segurança e os hotfixes do .NET Framework que estão instalados em um computador usando o PowerShell:

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){

   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

O exemplo produz uma saída semelhante à seguinte:

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a>Confira também

- [Como: Determinar quais versões do .NET Framework estão instaladas](how-to-determine-which-versions-are-installed.md)
- [Instalar o .NET Framework para desenvolvedores](../install/guide-for-developers.md)
- [Versões e dependências](versions-and-dependencies.md)
