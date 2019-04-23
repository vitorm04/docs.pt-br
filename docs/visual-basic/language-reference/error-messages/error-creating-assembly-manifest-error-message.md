---
title: 'Erro na criação de manifesto do assembly: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 0f67b772bab3104c00510954d01b200aadfa9e8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296284"
---
# <a name="error-creating-assembly-manifest-error-message"></a>Erro ao criar o manifesto do assembly: \<mensagem de erro >
O compilador do Visual Basic chama o vinculador de Assembly (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto. O vinculador reportou um erro no estágio de pré-emissão da criação do assembly.  
  
 Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado. Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas. Para marcar um atraso em um assembly, é necessário marcar a caixa de seleção **Somente sinal de atraso** e fornecer um arquivo de chave válido que contenha informações sobre as informações de chave pública. A chave privada não é necessária quando um assembly estiver marcado com atraso. Para obter mais informações, confira [Como: Assinar um assembly com um nome forte](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 **ID do erro:** BC30140  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). para o erro AL1019 mais explicações e aconselhamento  
  
2. Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também

- [Como: assinar um assembly com um nome forte](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Página de Assinatura, Designer de Projeto](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Fale conosco](/visualstudio/ide/talk-to-us)
