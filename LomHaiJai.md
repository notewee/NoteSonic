use_bpm 80

use_synth :pretty_bell


lp1 = [ :g4, :e5, :g5, :e5, :r, :g4, :g5, :d5, :c5, :e5, :c5,
        :r, :d5, :e5, :f5, :e5, :d5, :c5, :a4, :r, :a4, :g4, :a4, :b4, :c5, :d5 ]
lp1.each do
  play lp1.tick
  sleep 0.5
end