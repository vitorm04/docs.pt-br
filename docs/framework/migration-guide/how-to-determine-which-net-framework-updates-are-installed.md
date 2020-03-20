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
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="b4964-103">Como determinar quais atualizações de segurança e hotfixes do .NET Framework estão instalados</span><span class="sxs-lookup"><span data-stu-id="b4964-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="b4964-104">Este artigo mostra como descobrir quais atualizações de segurança e hotfixes do .NET Framework estão instaladas em um computador.</span><span class="sxs-lookup"><span data-stu-id="b4964-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="b4964-105">Todas as técnicas mostradas neste artigo exigem uma conta com privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="b4964-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="b4964-106">Use o Editor de Registro</span><span class="sxs-lookup"><span data-stu-id="b4964-106">Use Registry Editor</span></span>

<span data-ttu-id="b4964-107">As atualizações de segurança e os hotfixes instalados para cada versão do .NET Framework instalado em um computador estão listadas no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="b4964-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="b4964-108">Você pode usar o programa Editor do Registro (*regedit.exe*) para exibir essas informações.</span><span class="sxs-lookup"><span data-stu-id="b4964-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="b4964-109">Abra o programa **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="b4964-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="b4964-110">Nas versões Windows 8 e posteriores, clique com o botão direito do mouse **Start** ![Screenshot do logotipo da chave do Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Logotipo do Windowskeyboard")e selecione **Executar**.</span><span class="sxs-lookup"><span data-stu-id="b4964-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="b4964-111">Na caixa **Abrir**, digite **regedit.exe** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4964-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="b4964-112">No Editor do Registro, abrir a seguinte subchave:</span><span class="sxs-lookup"><span data-stu-id="b4964-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="b4964-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="b4964-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="b4964-114">As atualizações instaladas estão listadas nas subchaves que identificam a versão do .NET Framework a que se aplicam.</span><span class="sxs-lookup"><span data-stu-id="b4964-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="b4964-115">Cada atualização é identificada por um número da Base de Dados de Conhecimento (KB).</span><span class="sxs-lookup"><span data-stu-id="b4964-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="b4964-116">No Editor do Registro, as versões do .NET Framework e as atualizações instaladas para cada versão são armazenadas em subchaves diferentes.</span><span class="sxs-lookup"><span data-stu-id="b4964-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="b4964-117">Para saber mais sobre como detectar os números da versão instalada, veja [Como determinar quais versões do .NET Framework estão instaladas](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="b4964-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="b4964-118">Consultar o registro usando código</span><span class="sxs-lookup"><span data-stu-id="b4964-118">Query the registry using code</span></span>

<span data-ttu-id="b4964-119">O exemplo a seguir determina programaticamente as atualizações de segurança e os hotfixes do .NET Framework que estão instalados em um computador:</span><span class="sxs-lookup"><span data-stu-id="b4964-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="b4964-120">O exemplo produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="b4964-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="b4964-121">Use o PowerShell para consultar o registro</span><span class="sxs-lookup"><span data-stu-id="b4964-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="b4964-122">O exemplo a seguir mostra como determinar as atualizações de segurança e os hotfixes do .NET Framework que estão instalados em um computador usando o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b4964-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="b4964-123">O exemplo produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="b4964-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4964-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4964-124">See also</span></span>

- [<span data-ttu-id="b4964-125">Como: Determinar quais versões do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="b4964-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="b4964-126">Instalar o .NET Framework para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="b4964-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="b4964-127">Versões e dependências</span><span class="sxs-lookup"><span data-stu-id="b4964-127">Versions and dependencies</span></span>](versions-and-dependencies.md)
