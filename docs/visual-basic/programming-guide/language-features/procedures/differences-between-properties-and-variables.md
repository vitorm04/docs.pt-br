---
title: "Diferen&#231;as entre propriedades e vari&#225;veis no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "propriedades [Visual Basic], e variáveis"
  - "propriedades [Visual Basic], definido"
  - "propriedades [Visual Basic], Valores"
  - "valores de propriedade"
  - "Valores, propriedades"
  - "variáveis [Visual Basic]"
  - "variáveis [Visual Basic], e propriedades"
  - "variáveis [Visual Basic], definição"
  - "código do Visual Basic, procedimentos"
  - "código do Visual Basic, propriedades"
  - "código do Visual Basic, variáveis"
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diferen&#231;as entre propriedades e vari&#225;veis no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Variáveis e Propriedades representam os valores que você pode acessar.  No entanto, existem diferenças no armazenamento e implementação.  
  
## As variáveis  
 Um *Variable* corresponde diretamente a um local da memória.  Você definir uma variável com uma instrução de declaração único.  Uma variável pode ser um  *variável local* , definido dentro de um procedimento e disponíveis apenas dentro desse procedimento, ou pode ser um  *variável de membro* , definidos em um módulo, estrutura ou classe, mas não dentro de qualquer procedimento.  Também é chamado um  *campo*  Um variável de membro.  
  
## Propriedades  
 Um *p roperty* é um elemento de dados definido em um módulo, classe ou estrutura.  Você define uma propriedade com um bloco de código entre o `Property` e `End Property` instruções.  O bloco de código contém um procedimento `Get`, um procedimento `Set` ou ambos.  Esses procedimentos são chamados  *Propriedade procedimentos*  ou os assessores da propriedade .  Além disso, para recuperar ou armazenar o valor da propriedade, eles também podem executar ações personalizadas, como atualizar um contador de acesso.  
  
## Diferenças  
 A tabela a seguir mostra algumas diferenças importantes entre as variáveis e propriedades.  
  
|Ponto de diferença|Variável|Propriedade|  
|------------------------|--------------|-----------------|  
|Declaração|Instrução de declaração único|Série de instruções em um bloco de código|  
|Implementação|Local de armazenamento único|Código executável \(propriedade procedimentos\)|  
|Armazenamento|Diretamente associados com valor da variável|Normalmente tem armazenamento interno não disponível fora da propriedade contendo classe ou módulo<br /><br /> Valor da Propriedade talvez ou pode não existir como um elemento armazenado <sup>1</sup>|  
|O código executável|Nenhum|Deve ter pelo menos um procedimento|  
|Leitura e Gravação acesso|Leitura\/gravação ou leitura \- somente|Leitura\/gravação ou leitura \- somente|  
|Ações Personalizadas \(adição para aceitar ou retornando valor\)|Não é possível|Pode ser realizada como parte da configuração ou recuperando valor da propriedade|  
  
 <sup>1</sup> diferentemente uma variável, o valor de uma propriedade pode não corresponder diretamente a um único item de armazenamento.  O armazenamento pode ser dividido em partes para conveniência ou segurança, ou o valor pode ser armazenado em um formulário criptografado.  Nesses casos o procedimento `Get` seria montar as peças ou descriptografar o valor armazenado, e o procedimento `Set` Criptografar o novo valor ou dividir o armazenamento constituintes\-lo.  Um valor da propriedade talvez efêmera, como hora do dia, no qual caso o procedimento `Get` calcularia\-lo sobre o instantaneamente sempre que você acessa a propriedade.  
  
## Consulte também  
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Como criar uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Como chamar um procedimento de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Como inserir um valor em uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [Como obter um valor a partir de uma propriedade](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)