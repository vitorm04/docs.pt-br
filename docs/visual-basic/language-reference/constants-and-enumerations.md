---
title: Constantes e enumerações (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: fcc3329d6e02a77bf54b5b9f08fddba1bc95ff54
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562627"
---
# <a name="constants-and-enumerations-visual-basic"></a>Constantes e enumerações (Visual Basic)
Visual Basic fornece um número de enumerações para desenvolvedores e constantes predefinidas. Constantes armazenam valores que permanecem constantes durante a execução de um aplicativo. Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes.  
  
## <a name="constants"></a>Constantes  
  
### <a name="conditional-compilation-constants"></a>Constantes de compilação condicional  
 A tabela a seguir lista as constantes predefinidas disponíveis para compilação condicional.  
  
|**Constante**|**Descrição**|  
|---|---|  
|`CONFIG`|Uma cadeia de caracteres que corresponde à configuração atual do **configuração da solução ativa** caixa a **Configuration Manager**.|  
|`DEBUG`|Um `Boolean` valor que pode ser definido na **propriedades do projeto** caixa de diálogo. Por padrão, a configuração de depuração para um projeto define `DEBUG`. Quando `DEBUG` for definido, <xref:System.Diagnostics.Debug> métodos de classe geram saída para o **saída** janela. Quando não estiver definido, <xref:System.Diagnostics.Debug> métodos de classe não são compilados e nenhuma saída de depuração será gerada.|  
|`TARGET`|Uma cadeia de caracteres que representa o tipo de saída para o projeto ou a configuração da linha de comando **/destino** opção. Os valores possíveis de `TARGET` são:<br /><br /> -"winexe" para um aplicativo do Windows.<br />-"exe" para um aplicativo de console.<br />-"library" para uma biblioteca de classes.<br />-"módulo" para um módulo.<br />-A **/destino** opção pode ser definida no ambiente de desenvolvimento integrado do Visual Studio. Para obter mais informações, consulte [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|Um `Boolean` valor que pode ser definido na **propriedades do projeto** caixa de diálogo. Por padrão, todas as configurações para um projeto definem `TRACE`. Quando `TRACE` for definido, <xref:System.Diagnostics.Trace> métodos de classe geram saída para o **saída** janela. Quando não estiver definido, <xref:System.Diagnostics.Trace> classe métodos não são compilados e nenhuma `Trace` saída é gerada.|  
|`VBC_VER`|Um número que representa a versão do Visual Basic, no *principais*. *pequenas* formato. O número de versão para [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] é 8.0.|  
  
### <a name="print-and-display-constants"></a>Imprimir e exibir constantes  
 Quando você chama impressão e exibe as funções, você pode usar as seguintes constantes em seu código no lugar dos valores reais.  
  
|**Constante**|**Descrição**|  
|---|---|  
|`vbCrLf`|Combinação de caracteres de avanço de linha/retorno de carro.|  
|`vbCr`|Caractere de retorno de carro.|  
|`vbLf`|Caractere de avanço de linha.|  
|`vbNewLine`|Caractere de nova linha.|  
|`vbNullChar`|Caractere nulo.|  
|`vbNullString`|Não é igual de uma cadeia de caracteres de comprimento zero (""); usado para chamar procedimentos externos.|  
|`vbObjectError`|Número do erro. Os números de erro definidos pelo usuário devem ser maiores que esse valor. Por exemplo:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Caractere de tabulação.|  
|`vbBack`|Caractere de BACKSPACE.|  
|`vbFormFeed`|Não usado no Microsoft Windows.|  
|`vbVerticalTab`|Não é útil no Microsoft Windows.|  
  
## <a name="enumerations"></a>Enumerações  
 A tabela a seguir lista e descreve as enumerações fornecidas pelo Visual Basic.  
  
|Enumeração|Descrição|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Indica o estilo da janela a ser usado para o programa invocado ao chamar a função <xref:Microsoft.VisualBasic.Interaction.Shell%2A>.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Indica como tocar sons ao chamar métodos de áudio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Indica o tipo de função a ser verificada ao chamar o método <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>.|  
|<xref:Microsoft.VisualBasic.CallType>|Indica o tipo de procedimento que está sendo invocado ao chamar a função <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Indica como comparar cadeias de caracteres ao chamar funções de comparação.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Indica como exibir datas ao chamar a função <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Indica como determinar e formatar intervalos de datas ao chamar funções relacionadas a datas.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Especifica o que deve ser feito quando um diretório que deve ser excluído contém arquivos ou diretórios.|  
|<xref:Microsoft.VisualBasic.DueDate>|Indica quando os pagamentos vencem ao chamar métodos financeiros.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Indica se os campos de texto são delimitados ou largura fixa.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Indica os atributos de arquivo a usar ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Indica o primeiro dia da semana a ser usado ao chamar funções relacionadas a datas.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Indica a primeira semana do ano a ser usada ao chamar funções relacionadas a datas.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Indica qual botão foi pressionado em uma caixa de mensagem, retornado pela função <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Indica quais botões exibir quando ao chamar a função <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Especifica se um arquivo deve ser excluído permanentemente ou colocado na Lixeira.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Especifica se deve pesquisar todos ou somente diretórios de alto nível.|  
|<xref:Microsoft.VisualBasic.TriState>|Indica um `Boolean` valor ou se o padrão deve ser usado ao chamar funções de formatação numérica.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Especifica o que deve ser feito se o usuário clica **Cancelar** durante uma operação.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Especifica se deve ou não mostrar uma caixa de diálogo de progresso quando copiar, excluir ou mover arquivos ou diretórios.|  
|<xref:Microsoft.VisualBasic.VariantType>|Indica o tipo de um objeto variante, retornado pela função <xref:Microsoft.VisualBasic.Information.VarType%2A>.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Indica qual tipo de conversão executar ao chamar a função <xref:Microsoft.VisualBasic.Strings.StrConv%2A>.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência da linguagem Visual Basic](../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../visual-basic/index.md)  
 [Visão Geral de Constantes](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Visão geral de Enumerações](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
