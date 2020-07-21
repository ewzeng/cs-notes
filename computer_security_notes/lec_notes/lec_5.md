cryptography: a way to provide formal guarantees in the presence of an attacker

usually algs public; keys private (kerkhoff's principle)

sym encryption: keygen(), enc(), dec(); want correctness (dec gets the correct msg) and hide all info except length of msg

the latter can be decribed by the IND-CPA security game: if adv gets to know a bunch of msgs (of their choosing) and their encryptions, can adv distinguish between the encryptions of two msgs of same length (i.e. tell which msg corresponds to which encryption) with prob > $1/2 + \varepsilon$

- if so, then partial info leakage (partial info leakage bad b/c if attacker knows extra side info, msg can be reconstructed)

- mathematically: no partial info leak = no adv should be able to distinguish two msgs based on their encryption

one-time pad (xor): secure if you use it only once (OTP IND-CPA)