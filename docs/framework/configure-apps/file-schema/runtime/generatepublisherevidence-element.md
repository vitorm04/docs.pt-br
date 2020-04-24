---
title: Elemento <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645353"
---
# <a name="generatepublisherevidence-element"></a>\<Elemento generatePublisherEvidence >
Especifica se o tempo <xref:System.Security.Policy.Publisher> de execução cria evidências para o segurança de acesso ao código (CAS).  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gerar>de evidências do Publisher**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo <xref:System.Security.Policy.Publisher> de execução cria evidências.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não cria <xref:System.Security.Policy.Publisher> evidências.|  
|`true`|Cria <xref:System.Security.Policy.Publisher> evidências. Esse é o padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do runtime.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> No Quadro .NET 4 e posterior, este elemento não tem efeito nos tempos de carga de montagem. Para obter mais informações, consulte a seção "Simplificação de políticas de segurança" em [Alterações de Segurança](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 O tempo de execução do idioma comum (CLR) tenta <xref:System.Security.Policy.Publisher> verificar a assinatura Authenticode na hora da carga para criar evidências para a montagem. No entanto, por padrão, <xref:System.Security.Policy.Publisher> a maioria dos aplicativos não precisa de provas. A política CAS padrão <xref:System.Security.Policy.PublisherMembershipCondition>não depende do . Você deve evitar o custo de inicialização desnecessário associado à verificação da assinatura do editor, a <xref:System.Security.Permissions.PublisherIdentityPermission> menos que seu aplicativo seja executado em um computador com política CAS personalizada ou esteja pretendendo satisfazer demandas em um ambiente de confiança parcial. (Demandas por permissões de identidade sempre têm sucesso em um ambiente de confiança total.)  
  
> [!NOTE]
> Recomendamos que os `<generatePublisherEvidence>` serviços usem o elemento para melhorar o desempenho da inicialização.  O uso desse elemento também pode ajudar a evitar atrasos que podem causar um intervalo e o cancelamento da inicialização do serviço.  
  
## <a name="configuration-file"></a>Arquivo de configuração  
 Este elemento só pode ser usado no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `<generatePublisherEvidence>` mostra como usar o elemento para desativar a verificação da política do editor CAS para um aplicativo.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações em tempo de execução](index.md)
- [Esquema de arquivo de configuração](../index.md)
