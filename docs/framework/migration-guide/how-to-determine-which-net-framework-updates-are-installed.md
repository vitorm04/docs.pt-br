---
title: "Como: determinar quais atualizações de segurança do .NET Framework e os hotfixes instalados"
description: "Saiba como determinar quais atualizações de segurança do .NET Framework e hotfixes são instalados em um computador."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c35705470a8e1b553eca2ca0c68d3b8b9b3f6fa6
ms.sourcegitcommit: a3ba258f7a8cab5c6d19a3743dd95e904ecebc44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Como: determinar quais atualizações de segurança do .NET Framework e os hotfixes instalados

Este artigo mostra como descobrir quais segurança do .NET Framework de atualizações e hotfixes são instalados em um computador.

> [!NOTE]
> Todas as técnicas mostradas neste artigo requerem uma conta com privilégios administrativos.

## <a name="to-find-installed-updates-using-the-registry"></a>Para localizar, instalar atualizações usando o registro

As atualizações de segurança instaladas e hotfixes para cada versão do .NET Framework instalado em um computador são listados no registro do Windows. Você pode usar o Editor do registro (*regedit.exe*) programa para exibir essas informações.

1. Abra o programa **regedit.exe**. No Windows 8 e versões posteriores, clique com botão direito **iniciar** ![de logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), em seguida, selecione **executar**. No **abrir** , digite **regedit** e selecione **Okey**.

2. No Editor do Registro, abrir a seguinte subchave:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     As atualizações instaladas estão listadas nas subchaves que identificam a versão do .NET Framework a que se aplicam. Cada atualização é identificada por um número da Base de Dados de Conhecimento (KB).

No Editor do Registro, as versões do .NET Framework e as atualizações instaladas para cada versão são armazenadas em subchaves diferentes. Para obter informações sobre como detectar os números de versão instalada, consulte [como: determinar quais versões do .NET Framework estão instaladas](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Para encontrar atualizações instaladas, consultando o registro no código

O exemplo a seguir determina programaticamente as atualizações de segurança do .NET Framework e hotfixes que são instalados em um computador:

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Para encontrar atualizações instaladas, consultando o registro no PowerShell

O exemplo a seguir mostra como determinar as atualizações de segurança do .NET Framework e hotfixes que são instalados em um computador usando o PowerShell:

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

O exemplo produz uma saída semelhante à seguinte:

```console
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Client Profile


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y


    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Extended


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y
```

## <a name="see-also"></a>Consulte também

[Como: determinar quais versões do .NET Framework estão instaladas](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md)  
[Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md)
