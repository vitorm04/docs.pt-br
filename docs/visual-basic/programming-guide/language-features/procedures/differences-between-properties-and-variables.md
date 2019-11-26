---
title: Diferenças entre Propriedades e Variáveis
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
ms.openlocfilehash: bbed3248840803d36607a67c8373fed15c07445f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341215"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Diferenças entre propriedades e variáveis no Visual Basic
Variables and properties both represent values that you can access. However, there are differences in storage and implementation.  
  
## <a name="variables"></a>Variáveis  
 A *variable* corresponds directly to a memory location. You define a variable with a single declaration statement. A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure. A member variable is also called a *field*.  
  
## <a name="properties"></a>Propriedades  
 A *property* is a data element defined on a module, class, or structure. You define a property with a code block between the `Property` and `End Property` statements. The code block contains a `Get` procedure, a `Set` procedure, or both. These procedures are called *property procedures* or *property accessors*. In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.  
  
## <a name="differences"></a>Differences  
 The following table shows some important differences between variables and properties.  
  
|Point of difference|Variável|propriedade|  
|-------------------------|--------------|--------------|  
|Declaração|Single declaration statement|Series of statements in a code block|  
|Implementação|Single storage location|Executable code (property procedures)|  
|Armazenamento|Directly associated with variable's value|Typically has internal storage not available outside the property's containing class or module<br /><br /> Property's value might or might not exist as a stored element <sup>1</sup>|  
|Executable code|Nenhum|Must have at least one procedure|  
|Read and write access|Read/write or read-only|Read/write, read-only, or write-only|  
|Custom actions (in addition to accepting or returning value)|Not possible|Can be performed as part of setting or retrieving property value|  
  
 <sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage. The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form. In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage. A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Como criar uma propriedade](./how-to-create-a-property.md)
- [Como declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
- Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
