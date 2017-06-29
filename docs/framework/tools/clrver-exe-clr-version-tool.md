---
title: "Clrver.exe (Ferramenta de Versão do CLR) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 2a3f1cf4d82aefc171d256dec166f0441e4fd57e
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (Ferramenta de Versão do CLR)
A ferramenta Versão do CLR (Clrver.exe) relata todas as versões instaladas do CLR (Common Language Runtime) no computador.  
  
 Essa ferramenta é instalada automaticamente com o Visual Studio. Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7). Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 No prompt de comando, digite o seguinte:  
  
## <a name="syntax"></a>Sintaxe  
  
```  
clrver [option]  
```  
  
## <a name="options"></a>Opções  
  
|Opção|Descrição|  
|------------|-----------------|  
|`-all`|Exibe todos os processos no computador que estão usando o CLR.|  
|*pid*|Exibe as versões do CLR usado pelo processo com a PID (ID de processo especificado).|  
|`-?`|Exibe sintaxe de comando e opções para a ferramenta.|  
  
## <a name="remarks"></a>Comentários  
 Se você chamar Clrver.exe sem opções, ele exibirá todas as versões do CLR instaladas. Se especificar uma PID para outro usuário, você deverá ter permissões administrativas para obter as informações da versão.  
  
> [!NOTE]
>  No Windows Vista e posterior, UAC (Controle de Conta de Usuário) determina os privilégios de um usuário. Se for um membro do grupo Administradores Internos, você receberá dois tokens de acesso do tempo de execução: um token de acesso do usuário padrão e um token de acesso do administrador. Por padrão, você está na função de usuário padrão. Para executar o código que exige a permissão administrativa, você deve primeiro elevar os privilégios do usuário padrão para o administrador. Você pode fazer isso ao iniciar o prompt de comando clicando com o botão direito do mouse no ícone do prompt de comando e indicando que você deseja executar como administrador.  
  
 A tentativa de determinar a versão do CLR dos processos SYSTEM, LOCAL SERVICE e NETWORK SERVICE resulta em uma mensagem indicando que a PID não existe.  
  
## <a name="examples"></a>Exemplos  
 O comando a seguir exibe todas as versões do CLR instaladas no computador.  
  
 `clrver`  
  
 O comando a seguir exibe a versão do CLR usada pelo processo 128.  
  
 `clrver 128`  
  
 O comando a seguir exibe todos os processos gerenciados e a versão do CLR que eles estão usando.  
  
 `Clrver -all`  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas](../../../docs/framework/tools/index.md)   
 [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

