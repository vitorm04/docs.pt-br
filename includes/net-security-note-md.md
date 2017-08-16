> [!CAUTION]
>  Segurança de Acesso do Código e Código Parcialmente Confiável  
>   
>  O .NET Framework fornece um mecanismo para a imposição de níveis variáveis de confiança em códigos diferentes em execução no mesmo aplicativo chamado CAS (Segurança de Acesso do Código).  O CAS no .NET Framework não deve ser usado como um mecanismo de imposição de limites de segurança com base na origem do código ou em outros aspectos da identidade. Estamos atualizando nossas diretrizes para refletir que o CAS e o Código Transparente de Segurança não terão suporte como um limite de segurança com código parcialmente confiável, especialmente o código de origem desconhecida. Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local.  
>   
>  Essa política é aplicável à todas as versões do .NET Framework, mas não é aplicável ao .NET Framework incluído no Silverlight.