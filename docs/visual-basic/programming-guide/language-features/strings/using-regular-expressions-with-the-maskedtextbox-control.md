---
title: Usando expressões regulares com o controle MaskedTextBox no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 25bdfaef300b001d1c052aeea4e1ad3547a6d3d7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43803802"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Usando expressões regulares com o controle MaskedTextBox no Visual Basic
Este exemplo demonstra como converter expressões regulares simples para trabalhar com o <xref:System.Windows.Forms.MaskedTextBox> controle.  
  
## <a name="description-of-the-masking-language"></a>Descrição da linguagem de mascaramento  
 O padrão <xref:System.Windows.Forms.MaskedTextBox> linguagem de mascaramento baseia-se na usada pelo `Masked Edit` controlar, no Visual Basic 6.0 e deve ser familiar aos usuários migrando desta plataforma.  
  
 O <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade do <xref:System.Windows.Forms.MaskedTextBox> controle especifica qual máscara de entrada usar. A máscara deve ser uma cadeia de caracteres composta de um ou mais elementos de máscara da tabela a seguir.  
  
|Elemento de mascaramento|Descrição|Elemento de expressão regular|  
|---------------------|-----------------|--------------------------------|  
|0|Qualquer dígito único entre 0 e 9. Entrada obrigatória.|\d|  
|9|Dígito ou espaço. Entrada opcional.|\d?|  
|#|Dígito ou espaço. Entrada opcional. Se essa posição é deixada em branco na máscara, ela será renderizada como um espaço. Sinal de mais (+) e subtração (-) são permitidos.|\d+-?|  
|L|Letra ASCII. Entrada obrigatória.|[a-zA-Z]|  
|?|Letra ASCII. Entrada opcional.|[a-zA-Z]?|  
|&|Caractere. Entrada obrigatória.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Caractere. Entrada opcional.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|Um|Alfanumérico. Entrada opcional.|\W|  
|.|Apropriado para decimal.|Não disponível.|  
|,|Cultura apropriado para milhares.|Não disponível.|  
|:|Separador de tempo apropriado.|Não disponível.|  
|/|Separador de data apropriado.|Não disponível.|  
|$|Símbolo de moeda apropriado.|Não disponível.|  
|\<|Converte todos os caracteres que seguem em minúsculas.|Não disponível.|  
|>|Converte todos os caracteres que seguem em maiusculas.|Não disponível.|  
|&#124;|Desfaz uma mudança anterior para cima ou baixo.|Não disponível.|  
|&#92;|Ignora um caractere de máscara, transformando-o em um literal. "\\\\" é a sequência de escape para uma barra invertida.|&#92;|  
|Todos os outros caracteres.|Literais. Todos os elementos não máscara aparecerá como eles próprios dentro <xref:System.Windows.Forms.MaskedTextBox>.|Todos os outros caracteres.|  
  
 O decimal (.), milhares (,), o tempo (:), data (/) e padrão de símbolos de moeda ($) para exibir esses símbolos, conforme definido pela cultura do aplicativo. Você pode forçá-los para exibir os símbolos para outra cultura usando o <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> propriedade.  
  
## <a name="regular-expressions-and-masks"></a>Expressões regulares e máscaras  
 Embora você possa usar expressões regulares e máscaras para validar a entrada do usuário, eles não são totalmente equivalentes. Expressões regulares podem expressar padrões mais complexos que máscaras, mas máscaras podem expressar as mesmas informações de forma mais sucinta e em um formato culturalmente relevante.  
  
 A tabela a seguir compara as quatro expressões regulares e a máscara equivalente para cada um.  
  
|Expressão regular|Máscara|Observações|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|O `/` caractere da máscara é um separador de data lógica, e ele será exibido ao usuário como o separador de data apropriado para a cultura atual do aplicativo.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Uma data (dia, abreviação de mês e ano) no formato de Estados Unidos, no qual a abreviação de mês de três letras é exibida com uma letra maiuscula inicial, seguida de duas letras minúsculas.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Número de telefone dos Estados Unidos, o código de área opcional. Se desejar que o usuário insere os caracteres opcionais, ela pode inserir espaços ou coloque o ponteiro do mouse diretamente na posição na máscara representada pelo primeiro 0.|  
|`$\d{6}.00`|`$999,999.00`|Um valor de moeda no intervalo de 0 a 999999. A moeda, milésimos e caracteres decimais serão substituídos no tempo de execução por seus equivalentes específicas da cultura.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)  
 [Controle MaskedTextBox](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
