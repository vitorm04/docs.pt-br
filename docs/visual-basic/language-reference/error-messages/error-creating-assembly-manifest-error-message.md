---
title: 'Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4032bbcbf9924eb5aad4e2cb1a6e74df9a472eca
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;
O compilador do Visual Basic chama o vinculador de Assembly (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto. O vinculador reportou um erro no estágio de pré-emissão da criação do assembly.  
  
 Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado. Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas. Para marcar um atraso em um assembly, é necessário marcar a caixa de seleção **Somente sinal de atraso** e fornecer um arquivo de chave válido que contenha informações sobre as informações de chave pública. A chave privada não é necessária quando um assembly estiver marcado com atraso. Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 **ID do erro:** BC30140  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro citada e consulte o tópico [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). Erro AL1019 mais explicações e conselhos  
  
2.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também  
 [Como assinar um assembly com um nome forte](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Página de Assinatura, Designer de Projeto](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Fale conosco](/visualstudio/ide/talk-to-us)
