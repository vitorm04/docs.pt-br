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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7032fd6005d5eccf27e0ca34cd89c050260d6e4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
Essa ferramenta de linha de comando fornece a capacidade de gerenciar o registro dos componentes do WCF e WF em um único computador. Em circunstâncias normais não será preciso usar essa ferramenta como WCF e componentes do WF são configuradas quando instalado. Mas se você estiver tendo problemas com a ativação do serviço, você pode tentar registrar os componentes usando esta ferramenta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Comentários  
 A ferramenta pode ser encontrada no seguinte local:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ de comunicação  
  
> [!NOTE]
>  Quando a ferramenta de registro de ServiceModel é executada em [!INCLUDE[wv](../../../includes/wv-md.md)], o **recursos do Windows** caixa de diálogo pode não refletir que o **Ativação HTTP do Windows Communication Foundation** opção em **Microsoft .NET Framework 3.0** está ativado. O **recursos do Windows** caixa de diálogo pode ser acessada clicando **iniciar**, em seguida, clique em **executar** e, em seguida, digitando **OptionalFeatures**.  
  
 As tabelas a seguir descrevem as opções que podem ser usadas com ServiceModelReg.exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`-ia`|Instala todos os componentes do WCF e WF.|  
|`-ua`|Desinstala todos os componentes do WCF e WF.|  
|`-r`|Repara todos os componentes do WCF e WF.|  
|`-i`|Instala componentes do WCF e WF especificados com-c.|  
|`-u`|Desinstala os componentes do WCF e WF especificados com-c.|  
|`-c`|Instala ou desinstala um componente:<br /><br /> -httpnamespace – reserva de Namespace HTTP<br />serviço de compartilhamento de porta - tcpportsharing – TCP<br />serviço de ativação de - tcpactivation – TCP (sem suporte no .NET 4 Client Profile)<br />serviço de ativação de pipe nomeado de - namedpipeactivation – (sem suporte no .NET 4 Client Profile<br />serviço de ativação - msmqactivation – MSMQ (sem suporte no .NET 4 Client Profile<br />manifestos de rastreamento de eventos - etw – ETW (Windows Vista ou posterior)|  
|`-q`|Modo silencioso (log de erros de exibição somente)|  
|`-v`|Modo detalhado.|  
|`-nologo`|Suprime a mensagem de direitos autoral e faixa.|  
|`-?`|Exibe o texto de ajuda|  
  
## <a name="fixing-the-fileloadexception-error"></a>Corrigir o erro FileLoadException  
 Se você instalou versões anteriores do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] em seu computador, você pode obter um `FileLoadFoundException` erro ao executar a ferramenta ServiceModelReg para registrar uma nova instalação. Isso pode ocorrer mesmo que você manualmente arquivos removidos da instalação anterior, mas intacto as configurações de Machine. config.  
  
 A mensagem de erro é semelhante ao seguinte.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Você deve observar da mensagem de erro que o assembly System. ServiceModel versão 2.0.0.0 foi instalado por uma versão inicial do Customer Technology Preview (CTP). A versão atual do assembly System. ServiceModel liberado é 3.0.0.0 em vez disso. Portanto, esse problema é encontrado quando você deseja instalar o oficial [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] versão em um computador em que versão de um CTP anterior do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] foi instalado, mas não completamente desinstalado.  
  
 ServiceModelReg.exe não é possível limpar as entradas da versão anterior, nem pode ele entradas de registro da nova versão. É a única solução alternativa editar manualmente o Machine. config. Você pode localizar o arquivo no local a seguir.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Se você estiver executando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] em um computador de 64 bits, você deve editar o arquivo mesmo neste local.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Localize todos os nós XML neste arquivo que fazem referência a "System. ServiceModel, versão = 2.0.0.0", exclua-os e todos os nós filho. Salve o arquivo e execute novamente ServiceModelReg.exe resolve esse problema.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir mostram como usar as opções mais comuns da ferramenta ServiceModelReg.exe.  
  
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
