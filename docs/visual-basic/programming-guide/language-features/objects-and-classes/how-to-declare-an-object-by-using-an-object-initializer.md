---
title: "Como declarar um objeto usando um inicializador de objeto (Visual Basic) | Microsoft Docs"
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
  - "declarando objetos usando o inicializador de objeto"
  - "inicializadores [Visual Basic]"
  - "inicializadores de objeto [Visual Basic]"
  - "Vídeo explicativo, Visual Basic"
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar um objeto usando um inicializador de objeto (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Inicializadores de objeto permitem que você declare e instancie uma instância de uma classe em uma única instrução.  Além disso, você pode inicializar um ou mais membros da instância ao mesmo tempo, sem chamar um construtor com parâmetros.  
  
 Quando você usa um inicializador de objeto para criar uma instância de um tipo nomeado, o construtor\-padrão para a classe é chamado, seguido pela inicialização dos membros designados na ordem que você especificar.  
  
 O procedimento a seguir mostra como criar uma instância de uma classe `Student` de três maneiras diferentes.  A classe tem primeiro nome, sobrenome e propriedades do ano da classe, entre outros.  Cada uma das três declarações cria uma nova instância de `Student`, com propriedade `First` definida como "Michael", propriedade `Last` definida como "Tucker", e todos os outros membros definidos com seus valores padrão.  O resultado de cada declaração no procedimento é equivalente ao exemplo a seguir, que não usa um inicializador de objeto.  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 Para obter uma implementação da classe `Student`, consulte [Como criar uma lista de itens](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md).  Você pode copiar o código daquele tópico para configurar a classe e criar uma lista de objetos `Student` para trabalhar.  
  
### Para criar um objeto de uma classe nomeada usando um inicializador de objeto  
  
1.  Comece a declaração como se você planejasse para usar um construtor.  
  
     `Dim student1 As New Student`  
  
2.  Digite a palavra\-chave `With`, seguida por uma lista de inicialização entre chaves.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  Na lista de inicialização, inclua cada propriedade que você deseja inicializar e atribua um valor inicial a ela.  O nome da propriedade é precedido por um ponto \(.\).  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     Você pode inicializar um ou mais membros da classe.  
  
4.  Como alternativa, você pode declarar uma nova instância da classe e, em seguida, atribuir um valor a ela.  Primeiro, declare uma instância de `Student`:  
  
     `Dim student2 As Student`  
  
5.  Inicie a criação de uma instância de `Student` na forma normal.  
  
     `Dim student2 As Student = New Student`  
  
6.  Digite `With` e, em seguida, um inicializador de objeto para inicializar um ou mais membros da nova instância.  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  Você pode simplificar a definição na etapa anterior omitindo `As Student`.  Se você fizer isso, o compilador determina que `student3` é uma instância de `Student` usando inferência de tipos locais.  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     Para obter mais informações, consulte [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## Consulte também  
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Como criar uma lista de itens](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md)   
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)