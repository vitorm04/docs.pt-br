---
title: Instrução End
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: cb2fb4abb21b7b9c6575cec4aca1374f63687607
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343730"
---
# <a name="end-statement"></a>Instrução End
Finaliza a execução imediatamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode posicionar a instrução de `End` em qualquer lugar em um procedimento para forçar o aplicativo inteiro a parar de ser executado. `End` fecha todos os arquivos abertos com uma instrução `Open` e limpa todas as variáveis do aplicativo. O aplicativo é fechado assim que não há nenhum outro programa contendo referências a seus objetos e nenhum de seus códigos está em execução.  
  
> [!NOTE]
> A instrução `End` interrompe a execução do código abruptamente e não invoca o `Dispose` ou o método `Finalize` ou qualquer outro código de Visual Basic. As referências de objeto mantidas por outros programas são invalidadas. Se uma instrução `End` for encontrada em um bloco `Try` ou `Catch`, o controle não passará para o bloco de `Finally` correspondente.  
  
 A instrução `Stop` suspende a execução, mas ao contrário de `End`, ela não fecha nenhum arquivo ou limpa nenhuma variável, a menos que seja encontrada em um arquivo executável compilado (. exe).  
  
 Como `End` encerra seu aplicativo sem participar de recursos que possam estar abertos, você deve tentar fechar corretamente antes de usá-lo. Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deverá fechá-lo antes que o controle atinja a instrução de `End`.  
  
 Você deve usar `End` com moderação e somente quando precisar parar imediatamente. As maneiras normais de encerrar um procedimento (instrução[Return](../../../visual-basic/language-reference/statements/return-statement.md) e [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas fecham o procedimento de forma limpa, mas também dão ao código de chamada a oportunidade de fechar corretamente. Um aplicativo de console, por exemplo, pode simplesmente `Return` do procedimento `Main`.  
  
> [!IMPORTANT]
> A instrução `End` chama o método <xref:System.Environment.Exit%2A> da classe <xref:System.Environment> no namespace <xref:System>. <xref:System.Environment.Exit%2A> requer que você tenha a permissão `UnmanagedCode`. Se você não fizer isso, ocorrerá um erro <xref:System.Security.SecurityException>.  
  
 Quando seguido por uma palavra-chave adicional, [End \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento ou bloco apropriado. Por exemplo, `End Function` encerra a definição de um procedimento de `Function`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `End` para encerrar a execução de código se o usuário solicitá-la.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Notas para desenvolvedores de dispositivos inteligentes  
 Não há suporte para essa instrução.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Instrução End \<palavra-chave >](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
