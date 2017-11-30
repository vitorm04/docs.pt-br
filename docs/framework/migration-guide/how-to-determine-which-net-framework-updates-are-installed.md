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
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="2e104-103">Como: determinar quais atualizações de segurança do .NET Framework e os hotfixes instalados</span><span class="sxs-lookup"><span data-stu-id="2e104-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="2e104-104">Este artigo mostra como descobrir quais segurança do .NET Framework de atualizações e hotfixes são instalados em um computador.</span><span class="sxs-lookup"><span data-stu-id="2e104-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="2e104-105">Todas as técnicas mostradas neste artigo requerem uma conta com privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="2e104-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="2e104-106">Para localizar, instalar atualizações usando o registro</span><span class="sxs-lookup"><span data-stu-id="2e104-106">To find installed updates using the registry</span></span>

<span data-ttu-id="2e104-107">As atualizações de segurança instaladas e hotfixes para cada versão do .NET Framework instalado em um computador são listados no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="2e104-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="2e104-108">Você pode usar o Editor do registro (*regedit.exe*) programa para exibir essas informações.</span><span class="sxs-lookup"><span data-stu-id="2e104-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="2e104-109">Abra o programa **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="2e104-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="2e104-110">No Windows 8 e versões posteriores, clique com botão direito **iniciar** ![de logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), em seguida, selecione **executar**.</span><span class="sxs-lookup"><span data-stu-id="2e104-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="2e104-111">No **abrir** , digite **regedit** e selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="2e104-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="2e104-112">No Editor do Registro, abrir a seguinte subchave:</span><span class="sxs-lookup"><span data-stu-id="2e104-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="2e104-113">As atualizações instaladas estão listadas nas subchaves que identificam a versão do .NET Framework a que se aplicam.</span><span class="sxs-lookup"><span data-stu-id="2e104-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="2e104-114">Cada atualização é identificada por um número da Base de Dados de Conhecimento (KB).</span><span class="sxs-lookup"><span data-stu-id="2e104-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="2e104-115">No Editor do Registro, as versões do .NET Framework e as atualizações instaladas para cada versão são armazenadas em subchaves diferentes.</span><span class="sxs-lookup"><span data-stu-id="2e104-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="2e104-116">Para obter informações sobre como detectar os números de versão instalada, consulte [como: determinar quais versões do .NET Framework estão instaladas](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="2e104-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="2e104-117">Para encontrar atualizações instaladas, consultando o registro no código</span><span class="sxs-lookup"><span data-stu-id="2e104-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="2e104-118">O exemplo a seguir determina programaticamente as atualizações de segurança do .NET Framework e hotfixes que são instalados em um computador:</span><span class="sxs-lookup"><span data-stu-id="2e104-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="2e104-119">O exemplo produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="2e104-119">The example produces an output that's similar to the following one:</span></span>

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="2e104-120">Para encontrar atualizações instaladas, consultando o registro no PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e104-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="2e104-121">O exemplo a seguir mostra como determinar as atualizações de segurança do .NET Framework e hotfixes que são instalados em um computador usando o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2e104-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

<span data-ttu-id="2e104-122">O exemplo produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="2e104-122">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2e104-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e104-123">See also</span></span>

[<span data-ttu-id="2e104-124">Como: determinar quais versões do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="2e104-124">How to: Determine which .NET Framework versions are installed</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[<span data-ttu-id="2e104-125">Instalar o .NET Framework para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="2e104-125">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="2e104-126">Versões e dependências</span><span class="sxs-lookup"><span data-stu-id="2e104-126">Versions and dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
