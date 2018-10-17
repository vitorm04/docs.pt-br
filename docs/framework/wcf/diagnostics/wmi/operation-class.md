---
title: Classe de operação
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 16de8b25594896349ea546d3def52dd256fe5c70
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371583"
---
# <a name="operation-class"></a>Classe de operação
Operação  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe de operação não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe de operação tem as seguintes propriedades:  
  
### <a name="action"></a>Ação  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A ação WS-Addressing da mensagem de solicitação.  
  
### <a name="asyncpattern"></a>AsyncPattern  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica que uma operação é implementada de forma assíncrona usando um `Begin`[colchetes de abertura/fechamento] e `End`par de métodos de [colchetes angulares de abertura/fechamento] em um contrato de serviço.  
  
### <a name="behaviors"></a>Comportamentos  
 Tipo de dados: matriz de comportamento  
  
 Tipo de acesso: somente leitura  
  
 Os comportamentos associados a essa operação.  
  
### <a name="iscallback"></a>IsCallback  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 True quando a operação é uma operação de retorno de chamada.  
  
### <a name="isinitiating"></a>IsInitiating  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se o método implementa uma operação que pode iniciar uma sessão no servidor.  
  
### <a name="isoneway"></a>IsOneWay  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se uma operação retorna uma mensagem de resposta.  
  
### <a name="isterminating"></a>IsTerminating  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se uma operação retorna uma mensagem de resposta.  
  
### <a name="methodsignature"></a>MethodSignature  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A assinatura do método da operação.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome da operação.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Tipo de dados: matriz de cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Os tipos dos parâmetros da operação.  
  
### <a name="replyaction"></a>ReplyAction  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O valor da ação de SOAP para a mensagem de resposta da operação.  
  
### <a name="returntype"></a>Tipoderetorno  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O tipo de retorno da operação.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.OperationDescription>
