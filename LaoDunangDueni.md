use_synth :piano
s = 180/60 #tempo 60

attack=0.01
a0 = 0            #no sleep
a1 = s            #whole
a2 = s*0.5        #half
a3 = s*(0.5+0.25) #halfdot
a4 = s*0.25       #quater
a6 = s*(0.25+0.125) #quarterdot
a8 = s*0.125       #eighth

rlp1 = [ :b3, :d4, :g4, :g4, :e4, :e4, :d4, :b3, :d4, :d4, :r, :b3, :g4]
rtp1 = [  a6,  a8,  a1,  a4,  a4,  a8,  a8,  a4,  a1,  a4, a4,  a6,  a8]

rlp1.concat [ [:b3, :e4], :d4, :g3, :b3, :d4, :b3, :a3, :g3, :a3, :a3, :e4, :d4, [:c3, :e4, :g4], [:f4, :a4], [:g4, :b4], :g4]
rtp1.concat  [        a2,  a4,  a4,  a6,  a8,  a8,  a8,  a4,  a1,  a4,  a8,  a8,              a4,        a4,          a3,  a4]

rlp1.concat [ [:f4, :a4], :b4, :d5, [:f4,:a4], :b4, :a4, :g4, :e4, :g4, :b3, :d4, :e4, :g4, :e4, [:c4,:e4], :g4, [:c4, :e4], :d4]
rtp1.concat [         a4,  a8,  a8,        a8,  a8,  a8,  a8,  a3,  a4,  a3,  a4,  a2,  a4,  a4,        a6,  a8,         a4,  a4]


rlp1.concat [ :d4, :d4, :r, :b3, :d4]
rtp1.concat [  a1,  a4, a4,  a4,  a8]

gllp1 = [:g2, :d3,[:g3,:b3], :d3]
gltp1 = [a6,  a8,       a4,  a4]

d7llp1 =  [:d2, :d3, :f3, :d3]
d7ltp1 =  [ a6,  a8, a4, a4]

g7llp1 = [[:g3, :b3],[:g3,:b3]]
g7ltp1 = [        a2,       a2]

cllp1 = [:c3, :g3,[:c4,:e3], :g3]
cltp1 = [ a6,  a8,       a4,  a4]

emllp1 = [:e3, :g3, :b3]
emltp1 = [ a6,  a8,  a2]

amllp1 = [:a2, :e3, :b3]
amltp1 = [ a6,  a8,  a2]

live_loop :lhand do
  play :r
  wait a2
  3.times do
    gllp1.zip(gltp1).each do |gllp1, gltp1|
      play gllp1, sustain:gltp1*1.5
      sleep gltp1
    end
  end
  play :g2, sustain: a4*1.5
  sleep a4
  play :r
  sleep a4
  play :r
  sleep a2
  2.times do
    gllp1.zip(gltp1).each do |gllp1, gltp1|
      play gllp1, sustain:gltp1*1.5
      sleep gltp1
    end
  end
  1.times do
    d7llp1.zip(d7ltp1).each do |d7llp1, d7ltp1|
      play d7llp1, sustain: d7ltp1*1.5
      sleep d7ltp1
    end
  end
  play :d2 ,sustain: a4
  sleep a4
  play :r ,sustain: a4
  sleep a4
  play :a2 ,sustain: a4
  sleep a4
  play :d2 ,sustain: a4
  sleep a4

  play :g2 , sustain: a1
  sleep a8
  play :d3 , sustain: a8
  sleep a8
  play :g3 , sustain: a8
  sleep a8
  play :a3 , sustain: a8
  sleep a8
  play :b3 , sustain: a2
  sleep a2

  1.times do
    g7llp1.zip(g7ltp1).each do |g7llp1, g7ltp1|
      play g7llp1, sustain: g7ltp1*1.5
      sleep g7ltp1
    end
  end

  1.times do
    cllp1.zip(cltp1).each do |cllp1, cltp1|
      play cllp1, sustain: cltp1*1.5
      sleep cltp1
    end
  end

  1.times do
    gllp1.zip(gltp1).each do |gllp1, gltp1|
      play gllp1, sustain:gltp1*1.5
      sleep gltp1
    end
  end

  1.times do
    emllp1.zip(emltp1).each do |emllp1, emltp1|
      play emllp1, sustain:emltp1*1.5
      sleep emltp1
    end
  end

  1.times do
    amllp1.zip(amltp1).each do |amllp1, amltp1|
      play amllp1, sustain:amltp1*1.5
      sleep amltp1
    end
  end

  1.times do
    d7llp1.zip(d7ltp1).each do |d7llp1, d7ltp1|
      play d7llp1, sustain: d7ltp1*1.5
      sleep d7ltp1
    end
  end

  play :d3 ,sustain: a4
  sleep a4
  play :r
  sleep a4
  sleep a2

end

live_loop :rhand do
  rlp1.zip(rtp1).each do |rlp1, rtp1|
    play rlp1, sustain:rtp1*2, amp:3
    sleep rtp1
  end
end
