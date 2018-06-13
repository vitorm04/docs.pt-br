---
title: Diferenças entre propriedades e variáveis no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: 126e4baa2752ba7ccb5e8ff7b06a44839c1d0af2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651499"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Diferenças entre propriedades e variáveis no Visual Basic
Variáveis e propriedades representam valores que você pode acessar. No entanto, há diferenças no armazenamento e implementação.  
  
## <a name="variables"></a>Variáveis  
 Um *variável* corresponde diretamente a um local de memória. Você define uma variável com uma única declaração. Uma variável pode ser um *variável local*, definido dentro de um procedimento e disponíveis apenas dentro desse procedimento, ou pode ser um *variável membro*, definido em um módulo, classe ou estrutura, mas não dentro de qualquer procedimento. Também é chamada de uma variável de membro um *campo*.  
  
## <a name="properties"></a>Propriedades  
 Um *propriedade* é um elemento de dados definido em um módulo, classe ou estrutura. Você define uma propriedade com um bloco de código entre as `Property` e `End Property` instruções. O bloco de código contém um `Get` procedimento, uma `Set` procedimento, ou ambos. Esses procedimentos são chamados *procedimentos de propriedade* ou *acessadores de propriedade*. Além de recuperar ou armazenar o valor da propriedade, eles também podem executar ações personalizadas, como atualizar um contador de acesso.  
  
## <a name="differences"></a>Diferenças  
 A tabela a seguir mostra algumas diferenças importantes entre variáveis e propriedades.  
  
|Ponto de diferença|Variável|Propriedade|  
|-------------------------|--------------|--------------|  
|Declaração|Instrução de declaração único|Série de instruções em um bloco de código|  
|Implementação|Único local de armazenamento|Código executável (propriedade procedimentos)|  
|Armazenamento|Diretamente associados com o valor da variável|Normalmente tem armazenamento interno não está disponível fora da propriedade contendo classe ou módulo<br /><br /> Valor da propriedade talvez ou pode não existir como um elemento armazenado <sup>1</sup>|  
|Código executável|Nenhum|Deve ter pelo menos um procedimento|  
|Acesso de leitura e gravação|Leitura/gravação ou somente leitura|Leitura/gravação, somente leitura ou somente gravação|  
|Ações personalizadas (além de aceitar ou retornando valor)|Não é possível|Pode ser executado como parte da configuração ou recuperar o valor da propriedade|  
  
 <sup>1</sup> Diferentemente de uma variável, o valor de uma propriedade pode não corresponder diretamente a um único item de armazenamento. O armazenamento pode ser dividido em partes para conveniência ou segurança, ou o valor pode ser armazenado em um formato criptografado. Nesses casos o `Get` procedimento seria montar as peças ou descriptografar o valor armazenado e o `Set` procedimento criptografar o novo valor ou dividir o armazenamento constituinte-lo. Um valor de propriedade pode ser efêmero, como hora do dia, caso em que o `Get` procedimento seria calculá-lo dinamicamente sempre que você acessa a propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Como criar uma propriedade](./how-to-create-a-property.md)  
 [Como declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)  
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)  
 Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
