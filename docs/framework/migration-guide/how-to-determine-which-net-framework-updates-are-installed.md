---
title: "Como determinar quais atualizações do .NET Framework estão instaladas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba734dd3a9585b52b96cb2d27743da6190961126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a><span data-ttu-id="3ec48-102">Como determinar quais atualizações do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="3ec48-102">How to: Determine Which .NET Framework Updates Are Installed</span></span>
<span data-ttu-id="3ec48-103">As atualizações instaladas para cada versão do .NET Framework instalado em um computador estão listadas no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="3ec48-103">The installed updates for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="3ec48-104">Você pode usar o Editor do Registro (regedit.exe) para exibir essas informações.</span><span class="sxs-lookup"><span data-stu-id="3ec48-104">You can use the Registry Editor (regedit.exe) to view this information.</span></span>  
  
 <span data-ttu-id="3ec48-105">No Editor do Registro, as versões do .NET Framework e as atualizações instaladas para cada versão são armazenadas em subchaves diferentes.</span><span class="sxs-lookup"><span data-stu-id="3ec48-105">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="3ec48-106">Para saber mais sobre como detectar os números da versão instalada, veja [Como determinar quais versões do .NET Framework estão instaladas](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="3ec48-106">For information about detecting the installed version numbers, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span> <span data-ttu-id="3ec48-107">Para obter mais informações sobre como instalar o .NET Framework, consulte [Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="3ec48-107">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
### <a name="to-find-installed-updates"></a><span data-ttu-id="3ec48-108">Para localizar atualizações instaladas</span><span class="sxs-lookup"><span data-stu-id="3ec48-108">To find installed updates</span></span>  
  
1.  <span data-ttu-id="3ec48-109">Abra o programa **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="3ec48-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="3ec48-110">No Windows 8 e superior abra a tela Iniciar e digite o nome.</span><span class="sxs-lookup"><span data-stu-id="3ec48-110">In Windows 8 and higher open the Start screen and type the name.</span></span> <span data-ttu-id="3ec48-111">Em versões anteriores do Windows, no menu **Iniciar**, escolha **Executar** e, na caixa **Abrir**, digite **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="3ec48-111">In earlier versions of Windows, on the **Start** menu, choose **Run** and then, in the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="3ec48-112">Você deve ter credenciais administrativas para executar o regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="3ec48-112">You must have administrative credentials to run regedit.exe.</span></span>  
  
2.  <span data-ttu-id="3ec48-113">No Editor do Registro, abrir a seguinte subchave:</span><span class="sxs-lookup"><span data-stu-id="3ec48-113">In the Registry Editor, open the following subkey:</span></span>  
  
     <span data-ttu-id="3ec48-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span><span class="sxs-lookup"><span data-stu-id="3ec48-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span></span>  
  
     <span data-ttu-id="3ec48-115">As atualizações instaladas estão listadas nas subchaves que identificam a versão do .NET Framework a que se aplicam.</span><span class="sxs-lookup"><span data-stu-id="3ec48-115">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="3ec48-116">Cada atualização é identificada por um número da Base de Dados de Conhecimento (KB).</span><span class="sxs-lookup"><span data-stu-id="3ec48-116">Each update is identified by a Knowledge Base (KB) number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ec48-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ec48-117">Example</span></span>  
 <span data-ttu-id="3ec48-118">O código a seguir determina programaticamente as atualizações do .NET Framework instaladas em um computador.</span><span class="sxs-lookup"><span data-stu-id="3ec48-118">The following code programmatically determines the .NET Framework updates that are installed on a computer.</span></span> <span data-ttu-id="3ec48-119">Você precisa ter as credenciais administrativas para executar esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="3ec48-119">You must have administrative credentials to run this example.</span></span>  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)]
 [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 <span data-ttu-id="3ec48-120">O exemplo produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="3ec48-120">The example produces output that's similar to the following:</span></span>  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ec48-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ec48-121">See also</span></span>

<span data-ttu-id="3ec48-122">[Como determinar quais versões do .NET Framework estão instaladas](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="3ec48-122">[How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span></span>  
<span data-ttu-id="3ec48-123">[Instalando o .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="3ec48-123">[Installing the .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span></span>  
[<span data-ttu-id="3ec48-124">Versões e dependências</span><span class="sxs-lookup"><span data-stu-id="3ec48-124">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
