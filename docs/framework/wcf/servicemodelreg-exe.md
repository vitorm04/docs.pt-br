---
title: Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
description: Use essa ferramenta de linha de comando para gerenciar o registro de componentes WCF e WF em um único computador se você tiver problemas com a ativação do serviço.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245889"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="bb73c-103">Ferramenta de registro de ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="bb73c-103">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="bb73c-104">Essa ferramenta de linha de comando fornece a capacidade de gerenciar o registro de componentes WCF e WF em um único computador.</span><span class="sxs-lookup"><span data-stu-id="bb73c-104">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="bb73c-105">Em circunstâncias normais, não é necessário usar essa ferramenta, pois os componentes WCF e WF são configurados quando instalados.</span><span class="sxs-lookup"><span data-stu-id="bb73c-105">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="bb73c-106">Mas se você estiver enfrentando problemas com a ativação do serviço, poderá tentar registrar os componentes usando essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="bb73c-106">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb73c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb73c-107">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb73c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb73c-108">Remarks</span></span>  
 <span data-ttu-id="bb73c-109">A ferramenta pode ser encontrada no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="bb73c-109">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="bb73c-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="bb73c-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="bb73c-111">Quando a ferramenta de registro de ServiceModel é executada no Windows Vista, a caixa de diálogo **recursos do Windows** pode não refletir que a opção de **ativação de HTTP Windows Communication Foundation** em **Microsoft .NET Framework 3,0** está ativada.</span><span class="sxs-lookup"><span data-stu-id="bb73c-111">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="bb73c-112">A caixa de diálogo **recursos do Windows** pode ser acessada clicando em **Iniciar**, depois em **executar** e digitando **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="bb73c-112">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="bb73c-113">As tabelas a seguir descrevem as opções que podem ser usadas com ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="bb73c-113">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="bb73c-114">Opção</span><span class="sxs-lookup"><span data-stu-id="bb73c-114">Option</span></span>|<span data-ttu-id="bb73c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb73c-115">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="bb73c-116">Instala todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="bb73c-116">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="bb73c-117">Desinstala todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="bb73c-117">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="bb73c-118">Repara todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="bb73c-118">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="bb73c-119">Instala os componentes WCF e WF especificados com – c.</span><span class="sxs-lookup"><span data-stu-id="bb73c-119">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="bb73c-120">Desinstala os componentes WCF e WF especificados com – c.</span><span class="sxs-lookup"><span data-stu-id="bb73c-120">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="bb73c-121">Instala ou desinstala um componente:</span><span class="sxs-lookup"><span data-stu-id="bb73c-121">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="bb73c-122">-Httpnamespace – reserva de namespace HTTP</span><span class="sxs-lookup"><span data-stu-id="bb73c-122">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="bb73c-123">-tcpportsharing – serviço de compartilhamento de porta TCP</span><span class="sxs-lookup"><span data-stu-id="bb73c-123">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="bb73c-124">-tcpactivation – serviço de ativação TCP (sem suporte no perfil de cliente do .NET 4)</span><span class="sxs-lookup"><span data-stu-id="bb73c-124">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="bb73c-125">-namedpipeactivation – serviço de ativação de pipe nomeado (sem suporte no perfil de cliente do .NET 4</span><span class="sxs-lookup"><span data-stu-id="bb73c-125">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="bb73c-126">-MsmqActivation – serviço de ativação MSMQ (sem suporte no perfil do cliente .NET 4</span><span class="sxs-lookup"><span data-stu-id="bb73c-126">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="bb73c-127">-ETW – manifestos de rastreamento de eventos ETW (Windows Vista ou posterior)</span><span class="sxs-lookup"><span data-stu-id="bb73c-127">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="bb73c-128">Modo silencioso (somente exibir log de erros)</span><span class="sxs-lookup"><span data-stu-id="bb73c-128">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="bb73c-129">Modo detalhado.</span><span class="sxs-lookup"><span data-stu-id="bb73c-129">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="bb73c-130">Suprime a mensagem de direitos autorais e de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="bb73c-130">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="bb73c-131">Exibe o texto de ajuda</span><span class="sxs-lookup"><span data-stu-id="bb73c-131">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="bb73c-132">Corrigindo o erro fileuploadexception</span><span class="sxs-lookup"><span data-stu-id="bb73c-132">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="bb73c-133">Se você instalou versões anteriores do WCF em seu computador, poderá receber um `FileLoadFoundException` erro ao executar a ferramenta ServiceModelReg para registrar uma nova instalação.</span><span class="sxs-lookup"><span data-stu-id="bb73c-133">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="bb73c-134">Isso pode acontecer mesmo que você tenha removido manualmente os arquivos da instalação anterior, mas deixou as configurações de machine.config intactas.</span><span class="sxs-lookup"><span data-stu-id="bb73c-134">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="bb73c-135">A mensagem de erro é semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="bb73c-135">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="bb73c-136">Você deve observar a mensagem de erro informando que o assembly 2.0.0.0 da versão System. ServiceModel foi instalado por uma versão CTP (Customer Technology Preview) antecipada.</span><span class="sxs-lookup"><span data-stu-id="bb73c-136">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="bb73c-137">A versão atual do assembly System. ServiceModel lançada é 3.0.0.0 em vez disso.</span><span class="sxs-lookup"><span data-stu-id="bb73c-137">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="bb73c-138">Portanto, esse problema é encontrado quando você deseja instalar a versão oficial do WCF em um computador em que uma versão CTP inicial do WCF foi instalada, mas não completamente desinstalada.</span><span class="sxs-lookup"><span data-stu-id="bb73c-138">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="bb73c-139">ServiceModelReg.exe não pode limpar as entradas de versão anterior, nem registrar as entradas da nova versão.</span><span class="sxs-lookup"><span data-stu-id="bb73c-139">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="bb73c-140">A única solução alternativa é editar manualmente machine.config. Você pode localizar esse arquivo no seguinte local.</span><span class="sxs-lookup"><span data-stu-id="bb73c-140">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="bb73c-141">Se você estiver executando o WCF em um computador de 64 bits, também deverá editar o mesmo arquivo neste local.</span><span class="sxs-lookup"><span data-stu-id="bb73c-141">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="bb73c-142">Localize todos os nós XML neste arquivo que se referem a "System. ServiceModel, Version = 2.0.0.0", exclua-os e todos os nós filho.</span><span class="sxs-lookup"><span data-stu-id="bb73c-142">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="bb73c-143">Salve o arquivo e execute novamente ServiceModelReg.exe resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="bb73c-143">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bb73c-144">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bb73c-144">Examples</span></span>  
 <span data-ttu-id="bb73c-145">Os exemplos a seguir mostram como usar as opções mais comuns da ferramenta de ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="bb73c-145">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
