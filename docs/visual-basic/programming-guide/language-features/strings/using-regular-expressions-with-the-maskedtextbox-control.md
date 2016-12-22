---
title: "Usando express&#245;es regulares com o controle MaskedTextBox no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cadeias de caracteres {Visual Basic], edição mascarada"
  - "cadeias de caracteres {Visual Basic], expressões regulares"
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Usando express&#245;es regulares com o controle MaskedTextBox no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esse exemplo demonstra como converter expressões regulares simples para trabalhar com o controle <xref:System.Windows.Forms.MaskedTextBox>.  
  
## Descrição da Linguagem Máscara  
 O padrão <xref:System.Windows.Forms.MaskedTextBox> mascaramento idioma se baseia usada pelo `Masked Edit` controlar no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 e deve ser familiar aos usuários migrando nessa plataforma.  
  
 A propriedade <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> do controle <xref:System.Windows.Forms.MaskedTextBox> especifica qual máscara de entrada usar.  Essa máscara deve ser uma string composta por um ou mais elementos de máscara da seguinte tabela.  
  
|Elemento de Máscara|Descrição|Elemento de expressão regular|  
|-------------------------|---------------|-----------------------------------|  
|0|Qualquer único dígito entre 0 e 9.  Entrada requerida.|\\d|  
|9|Dígito ou espaço.  Entrada opcional.|\[\\d\]?|  
|\#|Dígito ou espaço.  Entrada opcional.  Se a posição é deixada vazia na máscara, ela será renderizada como um espaço.  Mais \(\+\) e menos \(\-\) são permitidos.|\[ \\d\+\-\]?|  
|L|Letra ASCII.  Entrada requerida.|\[a\-zA\-Z\]|  
|?|Letra ASCII.  Entrada opcional.|\[a\-zA\-Z\]?|  
|&|Caractere.  Entrada requerida.|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]|  
|C|Caractere.  Entrada opcional.|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]?|  
|A|Alfanumérico.  Entrada opcional.|\\W|  
|.|Local apropriado para decimal.|Não disponível.|  
|,|Local apropriado para milhares.|Não disponível.|  
|:|Separador de tempo apropriado.|Não disponível.|  
|\/|Separador de dada apropriado.|Não disponível.|  
|$|Símbolo de moeda apropriado.|Não disponível.|  
|\<|Converte todos os caracteres que seguem para caixa baixa.|Não disponível.|  
|\>|Converte todos os caracteres que seguem para caixa alta.|Não disponível.|  
|&#124;|Desfaz um shift alto ou baixo anterior.|Não disponível.|  
|\\|Libera um caractere de máscara, tornando\-o um literal. "  \\ \\ "é a seqüência de escape para uma barra invertida.|\\|  
|Todos outros caracteres.|Literais.  Todos elementos não máscara irão apares como eles mesmos dentro de <xref:System.Windows.Forms.MaskedTextBox>.|Todos outros caracteres.|  
  
 O padrão de símbolos decimal \(.\), milhares \(,\), tempo \(:\), data \(\/\), e moeda \($\) a aparecer são definidos pela localização da aplicação.  Você pode forçá\-los a mostrar símbolos de outra localização usando a propriedade <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>.  
  
## Expressões Regulares e Máscaras.  
 Apesar de que você pode usar expressões regulares e máscaras para validar a entrada do usuários, elas não são completamente equivalentes.  Expressões regulares podem expressar padrões mais complexos que máscaras, mas máscaras podem expressar a mesma informação de forma mais sucinta e num formato localmente relevante.  
  
 A seguinte tabela compara quatro expressões regulares e a máscara equivalente para cada.  
  
|Expressão Regular|Máscara|Anotações|  
|-----------------------|-------------|---------------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|O caractere `/` na máscara é um separador lógico de data, e irá aparecer ao usuário como um separador de data apropriado para a localização da aplicação.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Uma data \(dia, abreviação do mês e ano\) no formato americano em que a abreviação de mês de três letras é mostrada com a primeira letra maiúscula e as duas seguintes em minúsculas.|  
|`(\(\d{3}\)-)?  \d{3}-d{4}`|`(999)-000-0000`|Telefone nos EUA, código de área opcional.  Se o usuário não quer entrar os caracteres opcionais, ele pode entrar espaços ou colocar o mouse diretamente na posição na máscara representada pelo primeiro 0.|  
|`$\d{6}.00`|`$999,999.00`|Um valor de moeda no intervalo de 0 a 999999.  A moeda, milésimos e caracteres decimais serão substituídos no tempo de execução com seus equivalentes específicos da cultura.|  
  
## Consulte também  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox>   
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [Controle MaskedTextBox](../Topic/MaskedTextBox%20Control%20\(Windows%20Forms\).md)