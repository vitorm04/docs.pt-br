---
title: Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: aa9fc1b2338007db240fb10a9af35754107b07d0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424873"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="2dc95-102">Ferramenta de registro de ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="2dc95-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="2dc95-103">Essa ferramenta de linha de comando fornece a capacidade de gerenciar o registro de componentes WCF e WF em um único computador.</span><span class="sxs-lookup"><span data-stu-id="2dc95-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="2dc95-104">Em circunstâncias normais, não é necessário usar essa ferramenta, pois os componentes WCF e WF são configurados quando instalados.</span><span class="sxs-lookup"><span data-stu-id="2dc95-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="2dc95-105">Mas se você estiver enfrentando problemas com a ativação do serviço, poderá tentar registrar os componentes usando essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="2dc95-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc95-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2dc95-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="2dc95-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2dc95-107">Remarks</span></span>  
 <span data-ttu-id="2dc95-108">A ferramenta pode ser encontrada no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="2dc95-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="2dc95-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="2dc95-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="2dc95-110">Quando a ferramenta de registro de ServiceModel é executada no [!INCLUDE[wv](../../../includes/wv-md.md)], a caixa de diálogo **recursos do Windows** pode não refletir que a opção de **ativação de HTTP Windows Communication Foundation** em **Microsoft .NET Framework 3,0** está ativada.</span><span class="sxs-lookup"><span data-stu-id="2dc95-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="2dc95-111">A caixa de diálogo **recursos do Windows** pode ser acessada clicando em **Iniciar**, depois em **executar** e digitando **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="2dc95-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="2dc95-112">As tabelas a seguir descrevem as opções que podem ser usadas com ServiceModelReg. exe.</span><span class="sxs-lookup"><span data-stu-id="2dc95-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="2dc95-113">Opção</span><span class="sxs-lookup"><span data-stu-id="2dc95-113">Option</span></span>|<span data-ttu-id="2dc95-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2dc95-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="2dc95-115">Instala todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="2dc95-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="2dc95-116">Desinstala todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="2dc95-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="2dc95-117">Repara todos os componentes WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="2dc95-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="2dc95-118">Instala os componentes WCF e WF especificados com – c.</span><span class="sxs-lookup"><span data-stu-id="2dc95-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="2dc95-119">Desinstala os componentes WCF e WF especificados com – c.</span><span class="sxs-lookup"><span data-stu-id="2dc95-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="2dc95-120">Instala ou desinstala um componente:</span><span class="sxs-lookup"><span data-stu-id="2dc95-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="2dc95-121">-Httpnamespace – reserva de namespace HTTP</span><span class="sxs-lookup"><span data-stu-id="2dc95-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="2dc95-122">-tcpportsharing – serviço de compartilhamento de porta TCP</span><span class="sxs-lookup"><span data-stu-id="2dc95-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="2dc95-123">-tcpactivation – serviço de ativação TCP (sem suporte no perfil de cliente do .NET 4)</span><span class="sxs-lookup"><span data-stu-id="2dc95-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="2dc95-124">-namedpipeactivation – serviço de ativação de pipe nomeado (sem suporte no perfil de cliente do .NET 4</span><span class="sxs-lookup"><span data-stu-id="2dc95-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="2dc95-125">-MsmqActivation – serviço de ativação MSMQ (sem suporte no perfil do cliente .NET 4</span><span class="sxs-lookup"><span data-stu-id="2dc95-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="2dc95-126">-ETW – manifestos de rastreamento de eventos ETW (Windows Vista ou posterior)</span><span class="sxs-lookup"><span data-stu-id="2dc95-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="2dc95-127">Modo silencioso (somente exibir log de erros)</span><span class="sxs-lookup"><span data-stu-id="2dc95-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="2dc95-128">modo detalhado.</span><span class="sxs-lookup"><span data-stu-id="2dc95-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="2dc95-129">Suprime a mensagem de direitos autorais e de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="2dc95-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="2dc95-130">Exibe o texto de ajuda</span><span class="sxs-lookup"><span data-stu-id="2dc95-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="2dc95-131">Corrigindo o erro fileuploadexception</span><span class="sxs-lookup"><span data-stu-id="2dc95-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="2dc95-132">Se você instalou versões anteriores do WCF em seu computador, poderá obter um erro de `FileLoadFoundException` ao executar a ferramenta ServiceModelReg para registrar uma nova instalação.</span><span class="sxs-lookup"><span data-stu-id="2dc95-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="2dc95-133">Isso pode acontecer mesmo que você tenha removido manualmente os arquivos da instalação anterior, mas deixou as configurações de Machine. config intactas.</span><span class="sxs-lookup"><span data-stu-id="2dc95-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="2dc95-134">A mensagem de erro é semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="2dc95-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="2dc95-135">Você deve observar a mensagem de erro informando que o assembly 2.0.0.0 da versão System. ServiceModel foi instalado por uma versão CTP (Customer Technology Preview) antecipada.</span><span class="sxs-lookup"><span data-stu-id="2dc95-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="2dc95-136">A versão atual do assembly System. ServiceModel lançada é 3.0.0.0 em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2dc95-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="2dc95-137">Portanto, esse problema é encontrado quando você deseja instalar a versão oficial do WCF em um computador em que uma versão CTP inicial do WCF foi instalada, mas não completamente desinstalada.</span><span class="sxs-lookup"><span data-stu-id="2dc95-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="2dc95-138">ServiceModelReg. exe não pode limpar as entradas da versão anterior, nem registrar as entradas da nova versão.</span><span class="sxs-lookup"><span data-stu-id="2dc95-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="2dc95-139">A única solução alternativa é editar manualmente o Machine. config. Você pode localizar esse arquivo no seguinte local.</span><span class="sxs-lookup"><span data-stu-id="2dc95-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="2dc95-140">Se você estiver executando o WCF em um computador de 64 bits, também deverá editar o mesmo arquivo neste local.</span><span class="sxs-lookup"><span data-stu-id="2dc95-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="2dc95-141">Localize todos os nós XML neste arquivo que se referem a "System. ServiceModel, Version = 2.0.0.0", exclua-os e todos os nós filho.</span><span class="sxs-lookup"><span data-stu-id="2dc95-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="2dc95-142">Salve o arquivo e execute novamente o ServiceModelReg. exe resolve esse problema.</span><span class="sxs-lookup"><span data-stu-id="2dc95-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2dc95-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2dc95-143">Examples</span></span>  
 <span data-ttu-id="2dc95-144">Os exemplos a seguir mostram como usar as opções mais comuns da ferramenta ServiceModelReg. exe.</span><span class="sxs-lookup"><span data-stu-id="2dc95-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
