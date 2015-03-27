Initiator:
Upon init(M)
	Send(M to all neighbors) 
	If |N(v)| = 0 then Termination Detection
Upon “Ack” on link l
	Mark l as Ack’d
	If ∀u∈N(v) are Ack’d then Termination Detection
Non-Root Node:
Upon Receiving M on link l
	If parent = nil then
		parent := l
		Send M to N(v)/{l}
		If |N(v)|=1 then Send(“Ack” to l)
	else
		Send(“Ack” to l)
Upon Receiving “Ack” on link l
	Mark l as Ack’d
	If ∀u∈N(v)\{parent} are Ack’d then Send(“Ack” to parent)
