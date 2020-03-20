---
title: Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183101"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="dd47f-102">Ferramenta de registro de ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="dd47f-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="dd47f-103">Esta ferramenta de linha de comando fornece a capacidade de gerenciar o registro de componentes WCF e WF em uma única máquina.</span><span class="sxs-lookup"><span data-stu-id="dd47f-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="dd47f-104">Em circunstâncias normais, você não deve precisar usar esta ferramenta, pois os componentes WCF e WF são configurados quando instalados.</span><span class="sxs-lookup"><span data-stu-id="dd47f-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="dd47f-105">Mas se você estiver tendo problemas com a ativação do serviço, você pode tentar registrar os componentes usando esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="dd47f-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd47f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd47f-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="dd47f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd47f-107">Remarks</span></span>  
 <span data-ttu-id="dd47f-108">A ferramenta pode ser encontrada no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="dd47f-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="dd47f-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="dd47f-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="dd47f-110">Quando a ferramenta de registro ServiceModel é executada no Windows Vista, a caixa de diálogo Recursos do **Windows** pode não refletir que a opção **de ativação HTTP** da Windows Communication Foundation em **Microsoft .NET Framework 3.0** esteja ativada.</span><span class="sxs-lookup"><span data-stu-id="dd47f-110">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="dd47f-111">A caixa de diálogo Recursos do **Windows** pode ser acessada clicando **em Iniciar,** depois clique **em Executar** e, em seguida, digitando **Opcionais .**</span><span class="sxs-lookup"><span data-stu-id="dd47f-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="dd47f-112">As tabelas a seguir descrevem as opções que podem ser usadas com ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="dd47f-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="dd47f-113">Opção</span><span class="sxs-lookup"><span data-stu-id="dd47f-113">Option</span></span>|<span data-ttu-id="dd47f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd47f-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="dd47f-115">Instala todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="dd47f-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="dd47f-116">Desinstala todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="dd47f-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="dd47f-117">Repara todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="dd47f-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="dd47f-118">Instala componentes WCF e WF especificados com –c.</span><span class="sxs-lookup"><span data-stu-id="dd47f-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="dd47f-119">Desinstala os componentes WCF e WF especificados com –c.</span><span class="sxs-lookup"><span data-stu-id="dd47f-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="dd47f-120">Instala ou desinstala um componente:</span><span class="sxs-lookup"><span data-stu-id="dd47f-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="dd47f-121">- httpnamespace - HTTP Namespace Reservation</span><span class="sxs-lookup"><span data-stu-id="dd47f-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="dd47f-122">- tcpportsharing – Serviço de compartilhamento de portas TCP</span><span class="sxs-lookup"><span data-stu-id="dd47f-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="dd47f-123">- ativação tcp – serviço de ativação TCP (sem suporte no Perfil do Cliente .NET 4)</span><span class="sxs-lookup"><span data-stu-id="dd47f-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="dd47f-124">- nomeativação de tubos – Serviço de ativação de tubulação nomeado (sem suporte no Perfil do Cliente .NET 4</span><span class="sxs-lookup"><span data-stu-id="dd47f-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="dd47f-125">- msmqactivation – Serviço de ativação MSMQ (sem suporte no Perfil do Cliente .NET 4</span><span class="sxs-lookup"><span data-stu-id="dd47f-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="dd47f-126">- etw – ETW event tracing manifests (Windows Vista ou posterior)</span><span class="sxs-lookup"><span data-stu-id="dd47f-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="dd47f-127">Modo silencioso (apenas registro de erro de exibição)</span><span class="sxs-lookup"><span data-stu-id="dd47f-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="dd47f-128">Modo verbose.</span><span class="sxs-lookup"><span data-stu-id="dd47f-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="dd47f-129">Suprime os direitos autorais e a mensagem de banner.</span><span class="sxs-lookup"><span data-stu-id="dd47f-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="dd47f-130">Exibe texto de ajuda</span><span class="sxs-lookup"><span data-stu-id="dd47f-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="dd47f-131">Corrigindo o erro FileLoadException</span><span class="sxs-lookup"><span data-stu-id="dd47f-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="dd47f-132">Se você instalou versões anteriores do WCF em sua máquina, você pode obter um `FileLoadFoundException` erro ao executar a ferramenta ServiceModelReg para registrar uma nova instalação.</span><span class="sxs-lookup"><span data-stu-id="dd47f-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="dd47f-133">Isso pode acontecer mesmo se você tiver removido manualmente arquivos da instalação anterior, mas deixou as configurações da máquina.config intactas.</span><span class="sxs-lookup"><span data-stu-id="dd47f-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="dd47f-134">A mensagem de erro é semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="dd47f-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="dd47f-135">Você deve observar a partir da mensagem de erro que o conjunto System.ServiceModel Versão 2.0.0.0 foi instalado por uma versão inicial da Visualização de Tecnologia do Cliente (CTP).</span><span class="sxs-lookup"><span data-stu-id="dd47f-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="dd47f-136">A versão atual do conjunto System.ServiceModel lançada é 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="dd47f-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="dd47f-137">Portanto, este problema é encontrado quando você deseja instalar a versão oficial do WCF em uma máquina onde uma versão ctp inicial do WCF foi instalada, mas não completamente desinstalada.</span><span class="sxs-lookup"><span data-stu-id="dd47f-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="dd47f-138">ServiceModelReg.exe não pode limpar entradas de versão anteriores, nem pode registrar as entradas da nova versão.</span><span class="sxs-lookup"><span data-stu-id="dd47f-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="dd47f-139">A única solução é editar manualmente machine.config. Você pode localizar este arquivo no seguinte local.</span><span class="sxs-lookup"><span data-stu-id="dd47f-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="dd47f-140">Se você estiver executando o WCF em uma máquina de 64 bits, você também deve editar o mesmo arquivo neste local.</span><span class="sxs-lookup"><span data-stu-id="dd47f-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="dd47f-141">Localize quaisquer nós XML neste arquivo que se referem a "System.ServiceModel, Version=2.0.0.0", exclua-os e quaisquer nós de criança.</span><span class="sxs-lookup"><span data-stu-id="dd47f-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="dd47f-142">Salvar o arquivo e executar o ServiceModelReg.exe resolve esse problema.</span><span class="sxs-lookup"><span data-stu-id="dd47f-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dd47f-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dd47f-143">Examples</span></span>  
 <span data-ttu-id="dd47f-144">Os exemplos a seguir mostram como usar as opções mais comuns da ferramenta ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="dd47f-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
