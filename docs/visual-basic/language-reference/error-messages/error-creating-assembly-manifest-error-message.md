---
title: 'Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Erro ao criar o manifesto do assembly: &lt;mensagem de erro&gt;
O compilador [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto. O vinculador reportou um erro no estágio de pré-emissão da criação do assembly.  
  
 Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado. Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas. Para marcar um atraso em um assembly, é necessário marcar a caixa de seleção **Somente sinal de atraso** e fornecer um arquivo de chave válido que contenha informações sobre as informações de chave pública. A chave privada não é necessária quando um assembly estiver marcado com atraso. Para obter mais informações, consulte [como: assinar um Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **ID do erro:** BC30140  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro citada e consulte o tópico [Al.exe ferramenta erros e avisos](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para erro AL1019 para obter mais explicações e conselhos  
  
2.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também  
 [Como Assinar um Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [Página de Assinatura, Designer de Projeto](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex)  
 [Ferramenta de Al.exe erros e avisos](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [Fale conosco](/visualstudio/ide/talk-to-us)
