---
title: "-errorreport (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /errorreport
dev_langs:
- CSharp
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: 35
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 34e7e3b8c6a9f645ec1b359095c2d289afd1370a
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="errorreport-c-compiler-options"></a>/errorreport (opções do compilador C#)
Esta opção fornece uma maneira conveniente de relatar um erro interno do compilador do C# à Microsoft.  
  
> [!NOTE]
>  No Windows Vista e Windows Server 2008, as configurações de relatório de erros que você faz para o Visual Studio não substituem as configurações feitas pelo WER (Relatório de Erros do Windows). As configurações do WER sempre têm precedência sobre as configurações de relatório de erros do Visual Studio.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Arguments  
 **none**  
 Relatórios sobre erros internos do compilador não serão coletados ou enviados à Microsoft.  
  
 **prompt**  
 Solicita que você envie um relatório quando um erro interno do compilador for recebido. **prompt** é o padrão quando você compila um aplicativo no ambiente de desenvolvimento.  
  
 **queue**  
 Enfileira o relatório de erros. Quando você faz logon com credenciais administrativas, pode relatar falhas desde a última vez que você fez logon. Não será solicitado que você envie relatórios de falhas mais de uma vez a cada três dias. **queue** é o padrão quando você compila um aplicativo na linha de comando.  
  
 **send**  
 Envia automaticamente relatórios de erros internos do compilador para a Microsoft. Para habilitar essa opção, primeiro você deve concordar com a política de coleta de dados da Microsoft. Na primeira vez que você especificar **/errorreport:send** em um computador, uma mensagem de compilador indicará a um site que contém a política de coleta de dados da Microsoft.  
  
 Essa opção depende das configurações do Registro. Para obter informações sobre como definir os valores apropriados no Registro, consulte [Como ativar o relatório de erros automático nas ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695) no site do MSDN.  
  
## <a name="remarks"></a>Comentários  
 Um ICE (erro interno do compilador) ocorre quando o compilador não pode processar um arquivo de código-fonte. Quando um ICE ocorre, o compilador não produz um arquivo de saída ou qualquer diagnóstico útil que você pode usar para corrigir o código.  
  
 Em versões anteriores, quando você recebia um ICE, era incentivado a entrar em contato com o Microsoft Product Support Services para relatar o problema. Usando **/errorreport**, você pode fornecer informações do ICE à equipe do Visual C#. Os relatórios de erro podem ajudar a melhorar versões futuras do compilador.  
  
 A capacidade do usuário de enviar relatórios depende das permissões de política de usuário e de computador.  
  
 Para obter mais informações sobre o depurador de erro, consulte [Descrição da ferramenta Dr. Watson para Windows (Drwtsn32.exe)](http://go.microsoft.com/fwlink/?LinkId=147286).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto. Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Clique no botão **Avançado**.  
  
4.  Modifique a propriedade **Relatório de Erros do Compilador Interno**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
