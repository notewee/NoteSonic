use_synth :piano
s = 120/60 #tempo 60

attack=0.01
a0 = 0        #no sleep
a1 = s        #whole
a2 = s*0.5    #half
a3 = s*(0.5+0.25) #halfdot
a4 = s*0.25   #quater
a6 = s*(0.25+0.125) #quarterdot
a8 = s*0.125  #eighth

rlp1 = [ :b3, :d4, :g4, :g4, :e4, :e4, :d4, :c4, :d4, :d4, :r, :b3, :g4]
rtp1 = [  a6,  a8,  a1,  a4,  a4,  a8,  a8,  a4,  a1,  a4, a4,  a6,  a8]

rlp1.concat [ [:b3, :e4], :d4, :g3, :b3, :d4, :b3, :a3, :g3, :a3, :a3, :e4, :d4, [:c3, :e4, :g4], [:f4, :a4], [:g4, :b4], :g4]
rtp1.concat  [        a2,  a4,  a4,  a6,  a8,  a8,  a8,  a4,  a1,  a4,  a8,  a8,              a4,        a4,          a3,  a4]

#rlp1.concat [ [:f4, :a4], :b4, :d5, [:f4,:a4], :b4, :a4, :g4, :e4, :g4, :b3, :d4, :e4, :g4, :e4, [:c4,:e4], :g4, [:c4, :e4], :d4]
#rtp1.concat [         a4,  a8,  a8,        a8,  a8,  a8,  a8,  a3,  a4,  a3,  a4,  a2,  a4,  a4,        a6,  a8,         a4,  a4]


gllp1 = [:e2, :d3,[:g3,:b3], :d3]
gltp1 = [a6,  a8,       a4,  a4]
live_loop :lhand do
  play :r
  wait a2
  3.times do
    gllp1.zip(gltp1).each do |gllp1, gltp1|
      play gllp1, sustain:gltp1
      sleep gltp1
    end
  end
  play :e2, sustain: a4
  sleep a4
  play :r
  sleep a4
  play :r
  sleep a2
  2.times do
    gllp1.zip(gltp1).each do |gllp1, gltp1|
      play gllp1, sustain:gltp1
      sleep gltp1
    end
  end
end

rlp1.zip(rtp1).each do |rlp1, rtp1|
  play rlp1, sustain:rtp1
  sleep rtp1
end