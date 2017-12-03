---
title: Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cfe522817fdc9a2aea23b1c9e8dce3b658d892c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="2e40b-102">Ferramenta de registro de ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="2e40b-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="2e40b-103">Essa ferramenta de linha de comando fornece a capacidade de gerenciar o registro dos componentes do WCF e WF em um único computador.</span><span class="sxs-lookup"><span data-stu-id="2e40b-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="2e40b-104">Em circunstâncias normais não será preciso usar essa ferramenta como WCF e componentes do WF são configuradas quando instalado.</span><span class="sxs-lookup"><span data-stu-id="2e40b-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="2e40b-105">Mas se você estiver tendo problemas com a ativação do serviço, você pode tentar registrar os componentes usando esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="2e40b-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e40b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e40b-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="2e40b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e40b-107">Remarks</span></span>  
 <span data-ttu-id="2e40b-108">A ferramenta pode ser encontrada no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="2e40b-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="2e40b-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ de comunicação</span><span class="sxs-lookup"><span data-stu-id="2e40b-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e40b-110">Quando a ferramenta de registro de ServiceModel é executada em [!INCLUDE[wv](../../../includes/wv-md.md)], o **recursos do Windows** caixa de diálogo pode não refletir que o **Ativação HTTP do Windows Communication Foundation** opção em **Microsoft .NET Framework 3.0** está ativado.</span><span class="sxs-lookup"><span data-stu-id="2e40b-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="2e40b-111">O **recursos do Windows** caixa de diálogo pode ser acessada clicando **iniciar**, em seguida, clique em **executar** e, em seguida, digitando **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="2e40b-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="2e40b-112">As tabelas a seguir descrevem as opções que podem ser usadas com ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="2e40b-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="2e40b-113">Opção</span><span class="sxs-lookup"><span data-stu-id="2e40b-113">Option</span></span>|<span data-ttu-id="2e40b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e40b-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="2e40b-115">Instala todos os componentes do WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="2e40b-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="2e40b-116">Desinstala todos os componentes do WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="2e40b-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="2e40b-117">Repara todos os componentes do WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="2e40b-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="2e40b-118">Instala componentes do WCF e WF especificados com-c.</span><span class="sxs-lookup"><span data-stu-id="2e40b-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="2e40b-119">Desinstala os componentes do WCF e WF especificados com-c.</span><span class="sxs-lookup"><span data-stu-id="2e40b-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="2e40b-120">Instala ou desinstala um componente:</span><span class="sxs-lookup"><span data-stu-id="2e40b-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="2e40b-121">-httpnamespace – reserva de Namespace HTTP</span><span class="sxs-lookup"><span data-stu-id="2e40b-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="2e40b-122">serviço de compartilhamento de porta - tcpportsharing – TCP</span><span class="sxs-lookup"><span data-stu-id="2e40b-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="2e40b-123">serviço de ativação de - tcpactivation – TCP (sem suporte no .NET 4 Client Profile)</span><span class="sxs-lookup"><span data-stu-id="2e40b-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="2e40b-124">serviço de ativação de pipe nomeado de - namedpipeactivation – (sem suporte no .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="2e40b-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="2e40b-125">serviço de ativação - msmqactivation – MSMQ (sem suporte no .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="2e40b-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="2e40b-126">manifestos de rastreamento de eventos - etw – ETW (Windows Vista ou posterior)</span><span class="sxs-lookup"><span data-stu-id="2e40b-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="2e40b-127">Modo silencioso (log de erros de exibição somente)</span><span class="sxs-lookup"><span data-stu-id="2e40b-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="2e40b-128">Modo detalhado.</span><span class="sxs-lookup"><span data-stu-id="2e40b-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="2e40b-129">Suprime a mensagem de direitos autoral e faixa.</span><span class="sxs-lookup"><span data-stu-id="2e40b-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="2e40b-130">Exibe o texto de ajuda</span><span class="sxs-lookup"><span data-stu-id="2e40b-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="2e40b-131">Corrigir o erro FileLoadException</span><span class="sxs-lookup"><span data-stu-id="2e40b-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="2e40b-132">Se você instalou versões anteriores do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] em seu computador, você pode obter um `FileLoadFoundException` erro ao executar a ferramenta ServiceModelReg para registrar uma nova instalação.</span><span class="sxs-lookup"><span data-stu-id="2e40b-132">If you installed previous versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="2e40b-133">Isso pode ocorrer mesmo que você manualmente arquivos removidos da instalação anterior, mas intacto as configurações de Machine. config.</span><span class="sxs-lookup"><span data-stu-id="2e40b-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="2e40b-134">A mensagem de erro é semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="2e40b-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="2e40b-135">Você deve observar da mensagem de erro que o assembly System. ServiceModel versão 2.0.0.0 foi instalado por uma versão inicial do Customer Technology Preview (CTP).</span><span class="sxs-lookup"><span data-stu-id="2e40b-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="2e40b-136">A versão atual do assembly System. ServiceModel liberado é 3.0.0.0 em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2e40b-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="2e40b-137">Portanto, esse problema é encontrado quando você deseja instalar o oficial [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] versão em um computador em que versão de um CTP anterior do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] foi instalado, mas não completamente desinstalado.</span><span class="sxs-lookup"><span data-stu-id="2e40b-137">Therefore, this issue is encountered when you want to install the official [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] release on a machine where an early CTP release of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="2e40b-138">ServiceModelReg.exe não é possível limpar as entradas da versão anterior, nem pode ele entradas de registro da nova versão.</span><span class="sxs-lookup"><span data-stu-id="2e40b-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="2e40b-139">É a única solução alternativa editar manualmente o Machine. config. Você pode localizar o arquivo no local a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e40b-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="2e40b-140">Se você estiver executando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] em um computador de 64 bits, você deve editar o arquivo mesmo neste local.</span><span class="sxs-lookup"><span data-stu-id="2e40b-140">If you are running [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="2e40b-141">Localize todos os nós XML neste arquivo que fazem referência a "System. ServiceModel, versão = 2.0.0.0", exclua-os e todos os nós filho.</span><span class="sxs-lookup"><span data-stu-id="2e40b-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="2e40b-142">Salve o arquivo e execute novamente ServiceModelReg.exe resolve esse problema.</span><span class="sxs-lookup"><span data-stu-id="2e40b-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2e40b-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2e40b-143">Examples</span></span>  
 <span data-ttu-id="2e40b-144">Os exemplos a seguir mostram como usar as opções mais comuns da ferramenta ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="2e40b-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
