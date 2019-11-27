---
title: Executando tarefas com My.Application, My.Computer e My.User
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: fc9fd9093a3db4785bfc94719dbae9ec1d586050
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329587"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)

Os três objetos de `My` central que fornecem acesso às informações e à funcionalidade comumente usada são `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>) e `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Você pode usar esses objetos para acessar informações relacionadas ao aplicativo atual, ao computador em que o aplicativo está instalado ou ao usuário atual do aplicativo, respectivamente.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>Meu. aplicativo, meu. computador e meu. usuário  

 Os exemplos a seguir demonstram como as informações podem ser recuperadas usando `My`.  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Além de recuperar informações, os membros expostos por meio desses três objetos também permitem executar métodos relacionados a esse objeto. Por exemplo, você pode acessar uma variedade de métodos para manipular arquivos ou atualizar o registro por meio de `My.Computer`.  
  
 A e/s de arquivo é significativamente mais fácil e rápida com `My`, que inclui uma variedade de métodos e propriedades para manipular arquivos, diretórios e unidades. O objeto <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> permite que você leia de grandes arquivos estruturados que têm campos delimitados ou de largura fixa. Este exemplo abre o `TextFieldParser` `reader` e o usa para ler de `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application` permite que você altere a cultura do seu aplicativo. O exemplo a seguir demonstra como esse método pode ser chamado.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
