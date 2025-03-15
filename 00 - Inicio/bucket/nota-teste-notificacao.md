#todo

---
Nos teste do leadbank-api, aparecem algumas mensagens de propriedades não encontradas, algumas dessas são campo_usuario_simulacao_para_notificar e relacao_perfil_denominacao_para_notificar, afim de evitar esses alertas a implementação a seguir pode ajustar a resolver o problema (Verificar via getattr se a propriedade existe).

```python
def criar_e_enviar_notificacao_simulacao(self, simulacao: Simulacao):  
    try:  
        # campos_usuarios = simulacao.status.campo_usuario_simulacao_para_notificar.all() or None  
        # perfis_denominacao = simulacao.status.relacao_perfil_denominacao_para_notificar.all() or None  
        if campo_usuario_simulacao_para_notificar := getattr(simulacao.status, 'campo_usuario_simulacao_para_notificar', None):  
            campos_usuarios = campo_usuario_simulacao_para_notificar.all()  
  
        if relacao_perfil_denominacao_para_notificar := getattr(simulacao.status, 'relacao_perfil_denominacao_para_notificar', None):  
            perfis_denominacao = relacao_perfil_denominacao_para_notificar.all()
```