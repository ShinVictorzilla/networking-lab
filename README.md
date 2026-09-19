# networking-lab

# Laboratórios de Redes com Packet Tracer

## 📌 Objetivo
Documentar experimentos práticos realizados no Cisco Packet Tracer para consolidar conhecimentos em redes de computadores.

---

## 🔬 Experimento 1: Hub vs Switch

### Topologia
- **Hub:** 3 PCs conectados (PC5, PC6, PC7)
- **Switch:** 3 PCs conectados (PC2, PC3, PC4)

### O que foi testado
- Envio de pacote do PC5 para o PC6 (cenário com Hub)
- Envio de pacote do PC2 para o PC3 (cenário com Switch)

### Resultado
| Dispositivo | Comportamento |
|---|---|
| **Hub** | Inundou o tráfego para todos os dispositivos (PC7 recebeu, mas descartou). |
| **Switch** | Entregou o pacote apenas para o PC3, usando a tabela MAC. |

### Aprendizados
- Diferença entre Hub e Switch
- Domínio de colisão
- Tabela MAC
- Eficiência e segurança na camada 2

---

## 🔬 Experimento 2: Roteamento Básico (se você fez)

### Topologia
- 2 PCs + 1 Switch + 1 Roteador

### O que foi testado
- Configuração de IP, gateway e teste de ping entre redes.

### Resultado
- Ping funcionou entre os PCs de redes diferentes.

### Aprendizados
- Configuração de gateway padrão
- Roteamento básico
