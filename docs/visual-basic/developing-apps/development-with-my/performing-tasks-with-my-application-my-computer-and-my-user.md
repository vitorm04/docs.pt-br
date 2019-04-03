---
title: Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 0372fbf63f6d12e266674f92225183911aa4ca30
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834031"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)
Os três centrais `My` objetos que fornecem funcionalidades de acesso a informações e comumente usadas estão `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), e `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Você pode usar esses objetos para acessar as informações que estão relacionadas ao aplicativo atual, o que o aplicativo está instalado no computador ou o usuário atual do aplicativo, respectivamente.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, My. Computer e My. User  
 Os exemplos a seguir demonstram como informações podem ser recuperados usando `My`.  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Além de recuperar informações, os membros expostos através desses três objetos também permitem que você executar métodos relacionados a esse objeto. Por exemplo, você pode acessar uma variedade de métodos para manipular arquivos ou atualizar o registro por meio de `My.Computer`.  
  
 E/s de arquivos é significativamente mais fácil e mais rápido com `My`, que inclui uma variedade de métodos e propriedades para manipular arquivos, diretórios e unidades. O <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> objeto permite que você leia grandes estruturas de arquivos que têm delimitadas ou campos de largura fixa. Este exemplo abre o `TextFieldParser` `reader` e o usa para ler de `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application` permite que você alterar a cultura do seu aplicativo. O exemplo a seguir demonstra como esse método pode ser chamado.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
