---
title: "Propriedades e m&#233;todos sobrecarregados (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], métodos"
  - "classes [Visual Basic], propriedades"
  - "sobrecarga de método"
  - "métodos [Visual Basic], sobrecarga"
  - "nomes, vários procedimentos com mesmo"
  - "palavra-chave Overloads, membros sobrecarregados"
  - "procedimentos, vários com o mesmo nome"
  - "propriedades [Visual Basic], sobrecarga"
  - "sombreamento"
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedades e m&#233;todos sobrecarregados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Sobrecarga é a criação de mais de um procedimento, construtor de instância ou propriedade em uma classe com o mesmo nome mas tipos diferentes de argumento.  
  
## Uso de sobrecarga.  
 Sobrecarga é especialmente útil quando o seu modelo de objeto determina que você emprega nomes idênticos para obter os procedimentos que operam em diferentes tipos de dados.  Por exemplo, uma classe que pode exibir vários tipos de dados diferentes pode ter `Display` procedimentos que esta aparência:  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 Sem sobrecarga, você precisaria criar nomes distintos para cada procedimento, mesmo que eles fazem a mesma coisa, como mostrado a seguir:  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 Sobrecarga torna mais fácil de usar propriedades ou métodos, pois oferece uma variedade de tipos de dados que podem ser usados.  Por exemplo, a sobrecarga `Display` método discutido anteriormente pode ser chamado com qualquer uma das linhas de código a seguir:  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 Em tempo de execução, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chamadas o procedimento correto com base nos tipos de dados dos parâmetros você especificar.  
  
## Regras de sobrecarga.  
 Você pode criar um membro sobrecarregadas para uma classe, adicionando dois ou mais propriedades ou métodos com o mesmo nome.  Exceto para membros derivados sobrecarregados, cada membro sobrecarregadas deve ter listas de parâmetros diferentes e os itens a seguir não podem ser usados como um recurso diferencial ao sobrecarregar uma propriedade ou um procedimento:  
  
-   Modificadores, como `ByVal` ou `ByRef`, que se aplicam a um membro ou parâmetros do membro.  
  
-   Nomes dos parâmetros  
  
-   Tipos de procedimentos de retorno  
  
 O `Overloads` palavra\-chave é opcional quando a sobrecarga, mas se houver sobrecarregado membro usa a `Overloads` palavra\-chave e, em seguida, todos os outros membros sobrecarregados com o mesmo nome também devem especificar essa palavra\-chave.  
  
 Classes derivadas podem sobrecarregar membros herdados com membros que possuem parâmetros idênticos e tipos de parâmetro, um processo conhecido como  *sombreamento pelo nome e assinatura*.  Se a `Overloads` palavra\-chave é usada quando o efeito de sombra por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação na classe base, e todas as outras sobrecargas para esse membro estará disponíveis para as instâncias da classe derivada.  
  
 Se a `Overloads` palavra\-chave for omitido ao sobrecarregar um membro herdado com um membro que possui parâmetros idênticos e tipos de parâmetro, em seguida, a sobrecarga é chamado de  *sombreamento pelo nome,*.  Sombreamento pelo nome, substitui a implementação herdada de um membro e torna todas as outras sobrecargas indisponível para instâncias de classe derivada e suas decedents.  
  
 O `Overloads` e `Shadows` modificadores não podem ser usados com a mesma propriedade ou método.  
  
### Exemplo  
 O exemplo a seguir cria métodos sobrecarregados que aceitam tanto um `String` ou `Decimal` representação de um valor em moeda corrente e retornar uma seqüência de caracteres que contém o imposto sobre vendas.  
  
##### Para usar esse exemplo para criar um método sobrecarregado  
  
1.  Abra um novo projeto e adicione uma classe chamada `TaxClass`.  
  
2.  Adicione o seguinte código à classe `TaxClass`:  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  Adicione o seguinte procedimento para seu formulário.  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  Adicionar um botão para seu formulário e a chamada a `ShowTax` procedimento a partir do `Button1_Click` evento do botão.  
  
5.  Execute o projecto e clique no botão no formulário para testar a sobrecarga `ShowTax` procedimento.  
  
 Em tempo de execução, o compilador escolhe a função apropriada sobrecarregada que corresponde aos parâmetros que está sendo usados.  Quando você clica no botão, o método sobrecarregado é chamado pela primeira vez com um `Price` parâmetro que é uma seqüência de caracteres e a mensagem, "o preço é uma seqüência de caracteres.  Imposto é $5,12 "é exibida.  `TaxAmount`é chamado com um `Decimal` valor pela segunda vez e a mensagem, "o preço é um número Decimal.  Imposto é $5,12 "é exibida.  
  
## Consulte também  
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Noções básicas de herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)